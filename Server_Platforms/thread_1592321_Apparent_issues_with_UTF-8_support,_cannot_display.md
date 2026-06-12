---
title: "Apparent issues with UTF-8 support, cannot display non-latin characters"
date: 2010-10-10
forum: Server Platforms
---

### Post by redbmk on 2010-10-10
Hi,

I've been looking everywhere for a solution and have had no luck. I'm running Ubuntu server ( Linux yn 2.6.32-25-generic-pae #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 i686 GNU/Linux ) with apache2 and I can't seem to get my website to display Korean characters. I'm trying to help a friend who's modifying a Korean website. I used wget to download the files and they just show up on my screen as questions marks and weird characters, but not Korean symbols. 

I've only copied over a couple of the files so far but even if you take a look at the title or when you view the source if you look at the meta description or keywords you can clearly see the difference between these two websites (assuming your setup can display Korean characters, the first page displays correctly but not the second):
[http://www.gnbenglish.com/](http://www.gnbenglish.com/)
[http://dev.yelleknedarb.com/gnb/](http://dev.yelleknedarb.com/gnb/)

I found an example UTF-8 text file online that displays fine in Chrome on my Windows 7 machine ( [http://www.cl.cam.ac.uk/~mgk25/ucs/examples/UTF-8-demo.txt](http://www.cl.cam.ac.uk/~mgk25/ucs/examples/UTF-8-demo.txt) ) but when I copy it to my server it shows up very differently ( [http://dev.yelleknedarb.com/UTF-8-demo.txt](http://dev.yelleknedarb.com/UTF-8-demo.txt) ).

I thought at first the problem was with wget so I downloaded the file in Windows (which looks fine in Notepad++) and copied it over using Putty's FTP client. It still displays just as incorrectly though ( [http://dev.yelleknedarb.com/UTF-8-demo.txt.3](http://dev.yelleknedarb.com/UTF-8-demo.txt.3) ).

I changed /etc/apache2/conf.d/charset to contain the following line, then restarted, but that didn't seem to fix anything:
AddDefaultCharset UTF-8

Also, connected through Putty, when I use vim on the files they don't display the correct symbols, and if I edit one of the files that contains Korean characters it doesn't seem to edit correctly. I highlighted a "/" character and hit "x" and instead of deleting the "/" like you would expect, it changes the line from
... href="/style.css?20090803" ...
to
... href=thtml; charset=utf-8" ...

which is taken directly from the line below it. When I type the command "locale" I get the following:

LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

What's wrong with my setup? Do I need to change it out of en_US to something more generic? I'd like to be able to display any characters; not just English, and not just Korean. I would think as long as it's keeping the UTF-8 encoding it should display fine in a browser. Is it getting stripped down by wget or apache2? Thanks in advance for the help.

---

