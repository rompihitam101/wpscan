![alt text](http://dvwa.co.uk/images/wpscan_logo_407x80.png "WPScan - WordPress Security Scanner")

#### LICENSE

WPScan - WordPress Security Scanner
Copyright (C), 2011-2012  Ryan Dewhurst AKA ethicalhack3r

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

ryandewhurst at gmail

#### INSTALL

WPScan comes pre-installed on the following Linux distributions:

- [BackTrack Linux](http://www.backtrack-linux.org/) since version 5 R1 in the /pentest/web/wpscan/ directory. 
- [SamuraiWTF](http://samurai.inguardians.com/)
- [BackBox Linux](http://www.backbox.org/)

WPScan only supports Ruby => 1.9.

*Installing on Debian/Ubuntu:*

```sudo apt-get install libcurl4-gnutls-dev libopenssl-ruby```

``` sudo gem install typhoeus nokogiri json```

*Installing on other nix:* (not tested)

```sudo gem install typhoeus nokogiri json```

*Installing on Mac OSX:*

```sudo gem install typhoeus nokogiri json```

#### KNOWN ISSUES

  - Typhoeus segmentation fault
      Update curl to at least v7.21 (you may have to install it from sources)
      See http://code.google.com/p/wpscan/issues/detail?id=81

  - If you have one the following errors : "-bash: !t: event not found", "-bash: !u: event not found"
      It happens whith enumeration : just put the 't' or 'u' before the 'p!' : '-e tp!' instead of '-e p!t'

#### WPSCAN ARGUMENTS

    --url   | -u <target url>  The WordPress URL/domain to scan.

    --force | -f Forces WPScan to not check if the remote site is running WordPress.

    --enumerate | -e [option(s)]  Enumeration.
     option :
       u        usernames from id 1 to 10
       u[10-20] usernames from id 10 to 20 (you must write [] chars)
       p        plugins
       p!       only vulnerable plugins
       t        timthumbs
     Multiple values are allowed : '-e tp' will enumerate timthumbs and plugins
     If no option is supplied, the default is 'upt'

    --follow-redirection  If the target url has a redirection, it will be followed without asking if you wanted to do so or not

    --proxy  Supply a proxy in the format host:port (will override the one from conf/browser.conf.json)

    --wordlist | -w <wordlist>  Supply a wordlist for the password bruter and do the brute.

    --threads  | -t <number of threads>  The number of threads to use when multi-threading requests. (will override the value from conf/browser.conf.json)

    --username | -U <username>  Only brute force the supplied username.

    --help     | -h This help screen.

    --verbose  | -v Verbose output.

#### WPSCAN EXAMPLES

Do 'non-intrusive' checks...

```ruby wpscan.rb --url www.example.com```

Do wordlist password brute force on enumerated users using 50 threads...

```ruby wpscan.rb --url www.example.com --wordlist darkc0de.lst --threads 50```

Do wordlist password brute force on the 'admin' username only...

```ruby wpscan.rb --url www.example.com --wordlist darkc0de.lst --username admin```

Enumerate instaled plugins...

```ruby wpscan.rb --url www.example.com --enumerate p```

Run all enumeration tools...

```ruby wpscan.rb --url www.example.com --enumerate```

#### WPSTOOLS ARGUMENTS

    --help    | -h   This help screen.
    --Verbose | -v   Verbose output.
    --update  | -u   Update to the latest revision.
    --generate_plugin_list [number of pages]  Generate a new data/plugins.txt file. (supply number of *pages* to parse, default : 150)
    --gpl  Alias for --generate_plugin_list

#### WPSTOOLS EXAMPLES

Generate a new 'most popular' plugin list, up to 150 pages...

```ruby wpstools.rb --generate_plugin_list 150```

#### PROJECT HOME

www.wpscan.org

#### GIT REPOSITORY

https://github.com/wpscanteam/

#### ISSUES

https://github.com/wpscanteam/testpage/issues

#### SPONSOR

WPScan is sponsored by the [RandomStorm](http://www.randomstorm.com) Open Source Initiative.
