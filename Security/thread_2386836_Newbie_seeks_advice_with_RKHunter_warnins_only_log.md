---
title: "Newbie seeks advice with RKHunter warnins only log.  Should I be worried?"
date: 2018-03-11
forum: Security
---

### Post by jimijives on 2018-03-11
Hi, this is the output from a Warnings Only scan:

```
rachel@rach-ES1:~$ sudo rkhunter -c --enable all --disable none --rwo
[sudo] password for rachel: 
Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script, ASCII text executable
Warning: The following processes are using deleted files:
         Process: /usr/sbin/ModemManager    PID: 1014    File: /usr/sbin/ModemManager
         Process: /usr/lib/xorg/Xorg    PID: 1131    File: /memfd:xshmfence
         Process: /sbin/upstart    PID: 1617    File: /home/rachel/.cache/upstart/window-stack-bridge.log.1
         Process: /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon    PID: 1852    File: /home/rachel/.local/share/gvfs-metadata/root
         Process: /usr/lib/firefox/firefox    PID: 4085    File: /dev/shm/org.chromium.gi7iOh
         Process: /opt/pia/nwjs/64/pia_nw    PID: 4977    File: /dev/shm/.io.nwjs.JZ5yKH
         Process: /opt/pia/nwjs/64/pia_nw    PID: 5103    File: /dev/shm/.io.nwjs.uXGwwV
         Process: /usr/bin/unity-scope-loader    PID: 25120    File: /tmp/tmpfOKYDVF
         Process: /usr/lib/firefox/firefox    PID: 25316    File: /dev/shm/org.chromium.6GjLt4
Warning: File '/tmp/pia_route' (score: 221) contains some suspicious content and should be checked.
Warning: Checking for files with suspicious contents [ Warning ]
Warning: Process '/sbin/dhclient' (PID 1537) is listening on the network.
Warning: Suspicious file types found in /dev:
         /dev/shm/pulse-shm-950600615: data
         /dev/shm/pulse-shm-795197379: data
         /dev/shm/pulse-shm-1451540733: data
         /dev/shm/pulse-shm-1521314150: data
         /dev/shm/pulse-shm-3168840125: data
         /dev/shm/pulse-shm-1954646288: data
         /dev/shm/pulse-shm-1352793245: data
         /dev/shm/pulse-shm-2179920676: data
         /dev/shm/pulse-shm-383728995: data
         /dev/shm/pulse-shm-1281043193: data
         /dev/shm/pulse-shm-3563464466: AmigaOS bitmap font
         /dev/shm/ecryptfs-rachel-Private: ASCII text
         /dev/shm/pulse-shm-691126216: data
         /dev/shm/pulse-shm-2337038942: data
         /dev/shm/pulse-shm-1098559874: data
```


Hi, I recently got hacked so I'm still quite paranoid.  I've read that RKHunter can give false positives so I'm hoping that is what most of this is.
For instance I looked in this file: /dev/shm/ecryptfs-rachel-Private: ASCII text
and there was just the number 2 written in it.  I checked for Hidden Files but it was still just a single number 2 in that file which I have no clue about.

What is concerning me is the part about something listening on the network.  I don't know how to deal with that or the ModemManager warning either.
Oh yeah and the first warning mentions something being replaced by a script.  All I know about scripts is they run strings of commands and that's a little concerning too.

I can't open the pulse-shm files.

I hope someone can offer some advice please, I would be very grateful.

Thank you.

Hi, I looked at that script and I have no knowledge of programming.  It's quite a long line of commands but it mentions asking for the username and password.  This is the very end of it.

```
sub usage
{
    die <<"EOT";
Usage: $progname [-options] <url>...
    -m <method>   use method for the request (default is '$method')
    -f            make request even if $progname believes method is illegal
    -b <base>     Use the specified URL as base
    -t <timeout>  Set timeout value
    -i <time>     Set the If-Modified-Since header on the request
    -c <conttype> use this content-type for POST, PUT, CHECKIN
    -a            Use text mode for content I/O
    -p <proxyurl> use this as a proxy
    -P            don't load proxy settings from environment
    -H <header>   send this HTTP header (you can specify several)
    -C <username>:<password>
                  provide credentials for basic authentication

    -u            Display method and URL before any response
    -U            Display request headers (implies -u)
    -s            Display response status code
    -S            Display response status chain (implies -u)
    -e            Display response headers (implies -s)
    -E            Display whole chain of headers (implies -S and -U)
    -d            Do not display content
    -o <format>   Process HTML content in various ways

    -v            Show program version
    -h            Print this message
EOT
}
```

---

### Post by Habitual on 2018-03-12
"to avoid these warnings" section at [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)

---

### Post by jimijives on 2018-03-14
Hi Habitual, thanks very much for replying with that link.  I did not know it existed.  I'm sorry for the late response also.

In my case Windows assumes correctly #-o

I much prefer Ubuntu now but being a Windows user for 16 years it's quite a longer learning curve even though I appreciate Ubuntu is the most accesssible of distros for newbies.  Windows seemed to be reasurring because you just installed Bit Defender and Malwarebytes and thought everything was nice and cosy.  Which is kinda was until 6 months ago when my computers and phones got destroyed.

I'm hoping that even if I did get hacked now the vandals wouldn't be able to rewrite the firmware and hardware drivers as they are protected by the root access?

What I find interesting is Android is based on Linux but is apparently worse than Windows for vulnerabilities and if someone clever wants to target your phone you are basically helpless.  I mean Google found some vulnerabilities a few months ago, and a few of them Critical so they patched their Pixel phones about two weeks later.  Lenovo haven't patched mine yet and the information must be in the wild by now.  Google should make a central server where users of any Android equipment can download the patches themselves because manufacturers don't seem bothered which is a mystery.  I read Apple is much safer because they test every single app before it goes on their store.  But their phones are far more expensive than Android and don't do anything special.

Sorry, little tangent there.

Thanks again for your help.
Have a nice day.

---

### Post by Habitual on 2018-03-14
You're welcome,  Jim.

---

