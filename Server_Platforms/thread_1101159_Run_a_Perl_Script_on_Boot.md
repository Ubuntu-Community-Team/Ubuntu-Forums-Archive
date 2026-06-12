---
title: "Run a Perl Script on Boot"
date: 2009-03-20
forum: Server Platforms
---

### Post by pgn674 on 2009-03-20
I have an Ubuntu Server 8.10 system, and am trying to get HoTTProxy running on boot. It runs OK if I run it manually, as specified in their [documentation]("http://www.hottproxy.org/articles/LinuxEtc.html"), by running perl HoTTProxy.pl while in the folder that that Perl file is located in. I put a file init.d, as specified [here]("https://help.ubuntu.com/community/UbuntuBootupHowto"), and followed the instructions for making it executable and running the update-rc.d. The conntents of the file is here:```
#!/bin/bash
su - ticsalsog -c "perl /home/ticsalsog/HoTTProxy-Source-0.24.0.0/HoTTProxy.pl>&/home/ticsalsog/HoTTProxy-Source-0.24.0.0/startup.log"
```When I reboot and check the startup.log I have it making, it says```
Can't locate HoTTProxy_Add-In_Filters.pl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/ticsalsog/HoTTProxy-Source-0.24.0.0/HoTTProxy.pl line 49.
```So I take a look at the Perl script, and it starts out with a bunch of use's, then it has```
require 'HoTTProxy_Add-In_Filters.pl';          # Any user-defined filters can be put in here
```I checked, and that HoTTProxy_Add-In_Filters.pl file is in the same directory as the executing script. So it would seem that the script doesn't think to look in the folder that it's running from when I have it running on boot. But, it does look in its own folder if I run it manually when I'm logged in. Does anybody know any way to get the script to use its own folder as a search path when it's running from boot?

---

### Post by pgn674 on 2009-03-20
Well, I found one sort of workaround. I edited the HoTTProxy.pl file, and put in```
use lib '/home/ticsalsog/HoTTProxy-Source-0.24.0.0';
```just before the require statement. Then, I rebooted, and this time I got the error```
Cannot open config file HoTTProxy.conf in /home/ticsalsog.
Error: No such file or directory
Ending.
```in my startup.log. It looks like this happens because of the lines```
# We need the path to the present executable.  Under Win32 this is pretty
# positive using the Win32::GetFullPathName.  Under Linux and the like,
# it looks like $ENV{'PWD'} will get us what we want - suggestions?
my $path;
my $slash;
if ($^O eq 'MSWin32') {
        $path = Win32::GetFullPathName( $0 );
        ($path) = $path =~ m/^(.*)\\/;  # e.g. C:\data\programming\Perl\HoTTProxy (no trailing slash)

} else {
        $path = $ENV{'PWD'};
}
```So it would seem the use lib line doesn't help with the $ENV{'PWD'} thing. I'm hesitant to try and edit this, because for all I know after I fix this with a work-around, another bug will show up. Or, a rare bug will come up that only occurs when I use HoTTProxy in a certain way. No, what I really need is for my bash script in init.d to emulate as close as possible me being logged in and manually running the perl script right from its directory.

So, that brings me back to square one. Anybody know how to do this?

---

### Post by fixitdude on 2009-03-23
If you don't have anything in HoTTProxy_Add-In_Filters.pl it looks like you could just comment that whole "require" line out.

In your shell script you should cd into the working directory and then run it, or maybe tell perl what directory to use.

And it looks like /home/ticsalsog/HoTTProxy-Source-0.24.0.0 is where HoTTProxy.conf is at, not just /home/ticsalsog/

Don't give up so easy and read the errors that come back to you more carefully.



....
Vegas poker pay table tester perl script
[http://ubuntuforums.org/showthread.php?t=1103613](http://ubuntuforums.org/showthread.php?t=1103613)

---

### Post by pgn674 on 2009-03-24
fixitdude, thank you for the many suggestions.

I checked the HoTTProxy_Add-In_Filters.pl file. It looks like it performs some clean up to make sure the proxy avoids compatibility issues with some phones that might be using the proxy server. I'm guessing that if I do edit out that require line, or just embed the HoTTProxy_Add-In_Filters.pl file's code in place of the line, I will still have that second error with the $ENV{'PWD'}, anyway.

I thought that when I ran a Perl script, it uses the directory that the Perl script's file is in as the working directory no matter what, and it doesn't matter what directory your terminal or shell script happens to be browsing at the time? Oh, BTW, I had forgotten that the term working directory is used for this kind of thing, so I hadn't used it in my many searches of the internet for an answer. I'll try it and see if there's a difference. ...Oh wow, look at that.```
ticsalsog@pgn674:~$ perl ./HoTTProxy-Source-0.24.0.0/HoTTProxy.pl
Can't locate HoTTProxy_Add-In_Filters.pl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at ./HoTTProxy-Source-0.24.0.0/HoTTProxy.pl line 51.
ticsalsog@pgn674:~$ cd HoTTProxy-Source-0.24.0.0
ticsalsog@pgn674:~/HoTTProxy-Source-0.24.0.0$ perl HoTTProxy.pl 

HoTTProxy 0.24.0.0 - (c) 2005 Brian A. Blakley

This program is free for personal use but must be licensed for commercial use.
...
```Huh, I can't believe I never came across that before. OK, I'll try that cd thing in my shell script. I changed it to```
#!/bin/bash
cd /home/ticsalsog/HoTTProxy-Source-0.24.0.0
perl HoTTProxy.pl>&/home/ticsalsog/HoTTProxy-Source-0.24.0.0/startup.log
```and rebooted. I also took out the "use lib" line I had put in HoTTProxy.pl. It worked! Yay! Hmm, it makes me wonder. What If I just made HoTTProxy.pl executable, and instead of "perl HoTTProxy.pl" I just used "HoTTProxy.pl". It already has #!/usr/bin/perl as the first line. Would that make the change directory unnecessary? I might try that later.

For your next suggestion, I think it was looking for HoTTProxy.conf in /home/ticsalsog because in my init.d start up script I had used "su - ticsalsog -c" to make the perl command run under that user, in hopes that it would fix the working directory thing.

I'm not sure how I didn't read the errors carefully. For the HoTTProxy.conf error, I knew it was looking in the wrong directory for that file, and I speculated that "$ENV{'PWD'}" wasn't affect by my inserted "use lib" line, while "require" was. And I assure you, I did a lot of searching for an answer to my problems before giving up and resorting to making a post about it.

Again, thank you for your many suggestions, especially the cd one that worked :)

---

### Post by pgn674 on 2009-03-24
Alright, I tried the setting HoTTProxy.pl to executable and running it without perl thing, and it made no difference. Curiosity is satiated.

---

### Post by BkkBonanza on 2009-03-24
I'm not sure you should run this as su -. I think creates a shell and hence starts the script from the root home directory. Perhaps try running more normally as sudo. Not sure that will help but worth trying.

---

### Post by pgn674 on 2009-03-25
BkkBonaza, I took off the su - entirely to get it working with the cd. So now the init.d script is running as, I don't know, whoever runs init.d scripts on boot. But, it is working now, so that's OK.

---

### Post by fixitdude on 2009-03-28
You're welcome and glad it worked out, most if not all of the init scripts run as root anyway because it hasn't gotten to the point of being fully booted yet to allow users to log in, so no need to su anything I'm pretty sure.

---

