---
title: "scheduled webstream not recording"
date: 2009-10-14
forum: Server Platforms
---

### Post by gobbledigook on 2009-10-14
hi!

i record a webstream of a friends radio show for him, it is set up as a script run under cron and has worked flawlessly for a few months now. But over the last couple of weeks it has not recorded the stream, i have the script [**_here_**]("http://ubuntuforums.org/showthread.php?t=1084534") post #4, and below is a copy of the log which i had sent to a file in my home directory:

```
run-parts: executing /etc/cron.d//phonic_fm
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Server returned 404: File Not Found
Server returned 404:File Not Found
Failed to parse header.
Failed, exiting.
Server returned 404: File Not Found
No stream found to handle url http://icecast.commedia.org.uk:8000/phonic.mp3
kill: 24: No such process

Could not find "phonic.wav".
rm: cannot remove `phonic.wav': No such file or directory
run-parts: /etc/cron.d//phonic_fm exited with return code 1

```

and here is my crontab:

```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
02 10   * * 3   root    run-parts --verbose /etc/cron.d/ 2> /home/server/phonic_tmp/log_err
#


```

any ideas?

---

