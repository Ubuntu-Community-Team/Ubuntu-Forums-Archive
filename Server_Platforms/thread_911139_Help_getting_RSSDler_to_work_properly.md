---
title: "Help getting RSSDler to work properly"
date: 2008-09-05
forum: Server Platforms
---

### Post by Aberrix on 2008-09-05
I installed RSSDler ([Link]("http://code.google.com/p/rssdler/")) using these instructions ([Link]("http://code.google.com/p/rssdler/wiki/InstallInstructions")). I also took their configuration ([Link]("http://code.google.com/p/rssdler/wiki/CommentedConfig")) and edited for my own use.

here is my configuration;
```

# default config filename is config.txt in ~/.rssdler
# lines (like this one) starting with # are comments and
# will be ignored by the config parser
# the only required section (though the program won't do much without others)
# sections are denoted by a line starting with [
# then the name of the section, then ending with ]
# so this is the global section
[global]
# download files to this directory. Defaults to the working directory.
downloadDir = /download/.watch

# makes this the 'working directory' of RSSDler. anytime you specify a filename
# without an absolute path, it will be relative to this
workingDir = /home/aberrix/.rssdler

# if a file is smaller than this, it will not be downloaded.
# if filesize cannot be determined, this is ignored.
# Specified in MB. Remember 1024 MB == 1GB
# 0 means no minimum, as does "None" (w/o the quotes)
minSize = 10

# if a file is larger than this, it will not be downloaded.  Default is None
# though this line is ignored because it starts with a #
maxSize = None

# write messages to a log file. 0 is off, 1 is just error messages,
# 3 tells you when yo download something, 5 is very, very wordy. (default = 0)
log = 5
# where to write those log messages (default 'downloads.log')
logFile = downloads.log

# like log, only prints to the screen (errors to stderr, other to stdout)
# default 3
verbose = 3

# the place where a cookie file can be found. Default None.
# cookieFile = /home/user/.mozilla/firefox/user/cookies.txt

# type of cookie file to be found at above location. default MozillaCookieJar
# cookieType = MozillaCookieJar
# other possible types are:
# cookieType = LWPCookieJar
# only works if urllib = False
# cookieType = MSIECookieJar

#how long to wait between checking feeds (in minutes). Default 15.
scanMins = 15

# how long to wait between http requests (in seconds). Default 0
sleepTime = 0

# to exit after scanning all the feeds, or to keep looping. Default False.
runOnce = False

# set to true to avoid having to install mechanize.
# side effects described in help. Default False.
urllib = False

# the rest of the global options are described in the help,
# let's move on to a thread

###################
# each section represents a feed, except for the one called global.
# this is the thread: somesite
###################

# thepiratebay.org  TV Shows
link = http://rss.thepiratebay.org/205
maxSize = 1000
minSize = 10
directory = /downloads/.watch
regextrue = (Dirty.Jobs.S04|HDTV)

```

However it doesn't seem to actually read the feed? here are some verbose 5 logs of when I actually tried running it;

```

20080904.11:02 INFO     --- RSSDler 0.4.0
20080904.11:02 DEBUG    writing daemonInfo
20080904.11:02 INFO     [Waking up] Thu Sep  4 11:02:59 2008
20080904.11:02 DEBUG    checking working dir, maybe changing dir
20080904.11:02 INFO     Scanning threads
20080904.11:02 INFO     Processing took 0 seconds
20080904.11:02 INFO     [Sleeping] Thu Sep  4 11:02:59 2008
20080904.11:02 DEBUG    checking sleep
20080904.11:04 INFO     --- RSSDler 0.4.0
20080904.11:04 DEBUG    writing daemonInfo
20080904.11:04 INFO     [Waking up] Thu Sep  4 11:04:18 2008
20080904.11:04 DEBUG    checking working dir, maybe changing dir
20080904.11:04 INFO     Scanning threads
20080904.11:04 INFO     Processing took 0 seconds
20080904.11:04 INFO     [Sleeping] Thu Sep  4 11:04:18 2008
20080904.11:04 DEBUG    checking sleep

```

I'm not sure where I am going wrong? Is it my regex statement for searching the feed or do I have a configuration error somewhere? Any help is ***GREATLY*** appreciated! Thanks in advance!

---

