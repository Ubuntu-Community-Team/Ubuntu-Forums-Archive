---
title: "Problem on running update-alternative"
date: 2013-01-28
forum: Server Platforms
---

### Post by satimis on 2013-01-28
Hi all,

Ubuntu 12.04 desktop 64bit
Wordpress
Blackbird theme

I'm following below article to install "Blackbird"

Installing Processing in Ubuntu 12.04
[http://www.spacemig.com/2012/07/installing-processing-in-ubuntu-12-04/](http://www.spacemig.com/2012/07/installing-processing-in-ubuntu-12-04/)
to install Blackbird

and encountered problem on running;
$ sudo update-alternatives --install /usr/bin/javac javac```

update-alternatives: --install needs <link> <name> <path> <priority>

Usage: update-alternatives [<option> ...] <command>

Commands:
  --install <link> <name> <path> <priority>
    [--slave <link> <name> <path>] ...
                           add a group of alternatives to the system.
  --remove <name> <path>   remove <path> from the <name> group alternative.
  --remove-all <name>      remove <name> group from the alternatives system.
  --auto <name>            switch the master link <name> to automatic mode.
  --auto <name>            switch the master link <name> to automatic mode.
  --display <name>         display information about the <name> group.
  --query <name>           machine parseable version of --display <name>.
  --list <name>            display all targets of the <name> group.
  --get-selections         list master alternative names and their status.
  --set-selections         read alternative status from standard input.
  --config <name>          show alternatives for the <name> group and ask the
                           user to select which one to use.
  --set <name> <path>      set <path> as alternative for <name>.
  --all                    call --config on all alternatives.
<link> is the symlink pointing to /etc/alternatives/<name>.
  (e.g. /usr/bin/pager)
<name> is the master name for this link group.
  (e.g. pager)
<path> is the location of one of the alternative target files.
  (e.g. /usr/bin/less)
<priority> is an integer; options with higher numbers have higher priority in
  automatic mode.

Options:
  --altdir <directory>     change the alternatives directory.
  --admindir <directory>   change the administrative directory.
  --log <file>             change the log file.
  --force                  allow replacing files with alternative links.
  --skip-auto              skip prompt for alternatives correctly configured
                           in automatic mode (relevant for --config only)
  --verbose                verbose operation, more output.
  --quiet                  quiet operation, minimal output.
  --help                   show this help message.
  --version                show the version.

```

Please help.  TIA

satimis

---

