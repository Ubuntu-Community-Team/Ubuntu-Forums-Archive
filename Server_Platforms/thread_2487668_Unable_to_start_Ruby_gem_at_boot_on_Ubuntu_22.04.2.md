---
title: "Unable to start Ruby gem at boot on Ubuntu 22.04.2"
date: 2023-06-12
forum: Server Platforms
---

### Post by packetkicker on 2023-06-12
Hi,


I have installed Oxidized and can run directly in the console and works as expected as user oxidized using:

```
/home/oxidized/.rvm/gems/ruby-3.1.2/bin/oxidized
``` or ```
/home/oxidized/.rvm/gems/ruby-3.1.2/wrapper/oxidized
```

```
oxidized@host:~$ gem environment
RubyGems Environment:
  - RUBYGEMS VERSION: 3.3.7
  - RUBY VERSION: 3.1.2 (2022-04-12 patchlevel 20) [x86_64-linux]
  - INSTALLATION DIRECTORY: /home/oxidized/.rvm/gems/ruby-3.1.2
  - USER INSTALLATION DIRECTORY: /home/oxidized/.local/share/gem/ruby/3.1.0
  - RUBY EXECUTABLE: /home/oxidized/.rvm/rubies/ruby-3.1.2/bin/ruby
  - GIT EXECUTABLE: /usr/bin/git
  - EXECUTABLE DIRECTORY: /home/oxidized/.rvm/gems/ruby-3.1.2/bin
  - SPEC CACHE DIRECTORY: /home/oxidized/.local/share/gem/specs
  - SYSTEM CONFIGURATION DIRECTORY: /home/oxidized/.rvm/rubies/ruby-3.1.2/etc
  - RUBYGEMS PLATFORMS:
     - ruby
     - x86_64-linux
  - GEM PATHS:
     - /home/oxidized/.rvm/gems/ruby-3.1.2
     - /home/oxidized/.rvm/rubies/ruby-3.1.2/lib/ruby/gems/3.1.0
  - GEM CONFIGURATION:
     - :update_sources => true
     - :verbose => true
     - :backtrace => false
     - :bulk_threshold => 1000
  - REMOTE SOURCES:
     - https://rubygems.org/
  - SHELL PATH:
     - /home/oxidized/.rvm/gems/ruby-3.1.2/bin
     - /home/oxidized/.rvm/gems/ruby-3.1.2@global/bin
     - /home/oxidized/.rvm/rubies/ruby-3.1.2/bin
     - /usr/local/sbin
     - /usr/local/bin
     - /usr/sbin
     - /usr/bin
     - /sbin
     - /bin
     - /usr/games
     - /usr/local/games
     - /snap/bin
     - /home/oxidized/.rvm/bin
     - /home/oxidized/.rvm/bin



```

Tried creating the oxidized.service file under /etc/systemd/system as below:

```
[Unit]
Description=Oxidized - Network Device Configuration Backup Tool
After=network-online.target multi-user.target
Wants=network-online.target


[Service]
ExecStart=/home/oxidized/.rvm/gems/ruby-3.1.2/wrapper/oxidized
User=oxidized
KillSignal=SIGKILL
#Environment="OXIDIZED_HOME= /home/oxidized/.config"
Restart=on-failure
RestartSec=300s


[Install]
WantedBy=multi-user.target
```

On reboot checking /var/log/syslog:

```
Jun  8 08:27:37 ren-oxi-01 systemd[1453]: oxidized.service: Failed to locate executable /home/oxidized/.rvm/gems/ruby-3.1.2/wrapper/oxidized: No such file or directory
Jun  8 08:27:37 ren-oxi-01 systemd[1453]: oxidized.service: Failed at step EXEC spawning /home/oxidized/.rvm/gems/ruby-3.1.2/wrapper/oxidized: No such file or directory
Jun  8 08:27:37 ren-oxi-01 systemd[1]: oxidized.service: Main process exited, code=exited, status=203/EXEC
Jun  8 08:27:37 ren-oxi-01 systemd[1]: oxidized.service: Failed with result 'exit-code'.
```

Any pointers on where I am going wrong?

---

### Post by TheFu on 2023-06-12
Ensure that the script doesn't assume any environment variables and if the PWD is important (common for Ruby webapps), that the process has cd'd successfully to that directory and is running using the expected userid, not root.

BTW,  /home/oxidized/.rvm/gems/ruby-3.1.2/wrapper/oxidized doesn't exist or cannot be accessed due to permissions, so if that isn't correct, nothing will work.

I don't have any current Ruby skills and have never used/heard of oxidize before.  About a decade ago I did ruby on rails development and still run a webapp using it, created by others.  Getting the software stack setup for any specific ruby webapp was always a hassle.  I used rvm to keep things mostly self-contained and never used the system-ruby.  That was always asking for problems.

---

### Post by MAFoElffen on 2023-06-13
In the startup, it says your executible and script path is:
```

/home/oxidized/.rvm/gems/ruby-3.1.2/bin/
# which would mean the full path of the command is
/home/oxidized/.rvm/gems/ruby-3.1.2/bin/oxidized

```
But in your .service file, you incorrectly have it as:
```

/home/oxidized/.rvm/gems/ruby-3.1.2/wrapper/oxidized

```
Try changing it to the above and test it again...

---

