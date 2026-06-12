---
title: "New Internet accountability software: Net Responsibility"
date: 2007-09-13
forum: Ubuntu Christian Edition
---

### Post by mssever on 2007-09-13
> **roggan87 said:**
> [SIZE=4][COLOR=Red]NOTE! This is not the place to discuss Net Responsibility any more![/COLOR][/SIZE]

The best place is the [forum at our website]("http://www.netresponsibility.com/forum/"). Simply use your Net Responsibility account when you log in.

If you want to contact us in private, or having problems logging in using your account, you can use the [contact form]("http://www.netresponsibility.com/contact.php").

Thanks,
Robert

The above quote is the latest official word on this thread.

[SIZE=4][COLOR=Red]**Update: I'm no longer actively maintaining this software and others have taken over the project. Up-to-date information can be found on the [Net Responsibility website]("http://www.netresponsibility.com/"). The information below may or may not be outdated. Since I'm no longer active in this project, I don't know which it is.**[/COLOR][/SIZE]

I've been working on an Internet accountability program for Linux. The idea is to log the websites you visit, then periodically e-mail that log so someone else. It also writes a log entry when it is shutdown.

I'm looking for people to test it. Any comments (or code contributions) are welcome.

Still to do:
[LIST]
[*]Make a configuration GUI (partially completed, but on hold for now)
[*]Increase the intelligence of the shutdown logger
[*]Build a web service that will provide a friendlier, configurable way for the accountability partner to view the logs
[/LIST]
**Installation**
[I]
NOTE: I keep this post up to date, and it is the canonical place for installation instructions, usage, known bugs, etc. The discussion later in the thread often deals with specific issues and/or versions of Net Responsibility, so a given post might not contain current information.[/I]
[LIST=1]
[*]Download Net Responsibility. You can get the latest release from the [Sourceforge download page]("http://sourceforge.net/project/platformdownload.php?group_id=205710"). If you're feeling adventurous, you can use Subversion to check out the latest development version: ```
svn checkout https://responsibility.svn.sourceforge.net/svnroot/responsibility/trunk net-responsibility
```
[*]If you downloaded the .deb, simply install it. If you downloaded the source tarball, extract it and follow the directions in the README file.
[*]Run Applications > Internet > Configure Net Responsibility.
[/LIST]
[B]Running
[/B]
The core of Net Responsibility is a daemon that runs in the background. It is started automatically when you boot your computer. However, if you want to control it manually for testing purposes, here's how:
[LIST]
[*]Start ```
sudo net-responsibility-daemon
```
[*]Stop ```
sudo /etc/init.d/net-responsibility-daemon stop
```
[/LIST]
Net Accountability sends daily reports via e-mail. Be sure to set the proper e-mail addresses in the config file (/etc/net-responsibility.conf). The easiest way to accomplish this is by running Applications > Internet > Configure Net Responsibility. You can generate a report at any time by typing ```
sudo net-responsibility-report
```**Known Bugs**
Both net-responsibility-daemon and net-responsibility-report print an error message similar to the following to one or more of stderr, /var/log/syslog, or /var/log/daemon.log:```
net-responsibility-report[17580]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[17580]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[17580]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:153:in 'close'
net-responsibility-report[17580]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[17580]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[17580]: => from /usr/local/bin/net-responsibility-report:116
``` (The process name and ID vary, of course.) I haven't been able to solve this error yet, but I don't think that it's serious. Previously, I suppressed it, but I'm not comfortable with suppressing error messages.

---

### Post by mhancoc7 on 2007-09-13
> **mssever said:**
> I've been working on an Internet accountability program for Linux. The idea is to log the websites you visit, then periodically e-mail that log so someone else. It also writes a log entry when it is shutdown.

I'm looking for people to test it. Any comments (or code contributions) are welcome.

Still to do:[LIST]
[*]It doesn't actually send mail yet because I'm not sure yet what the best method to accomplish that is (suggestions are welcome)
[*]Make a configuration GUI
[*]Make a deb
[*]Make the reports more selective, perhaps by using a URL filter; also increase the intelligence of the shutdown logger[/LIST]**Installation**[LIST=1]
[*]Install the dependencies: ```
sudo aptitude install ruby dsniff libdaemonize-ruby
```
[*]Download and extract the attached file.
[*]Open a terminal, cd to the directory just created, and type ```
sudo ./install.sh
```[/LIST][B]Running
[/B]
The core of Net Responsibility is a daemon that runs in the background. It is started automatically when you boot your computer. However, if you want to control it manually for testing purposes, here's how:[LIST]
[*]Start ```
sudo /etc/init.d/net-responsibility-daemon start
```
[*]Stop ```
sudo /etc/init.d/net-responsibility-daemon stop
```[/LIST]If you want to monitor the log in real time: ```
sudo less /var/log/net-responsibility.log
```Then press <Shift>F.

Net Accountability sends weekly reports. Because it doesn't do real mail yet, the report will be mailed to your machine's root account. You can generate a report at any time by typing ```
sudo net-responsibility-report
```

This looks very promising. I will be watching this closely.

Thanks, Jereme

---

### Post by xilix on 2007-09-13
OK, now I have tested it. The installation worked and I can check the log file.

All visited websites and their parts are listed (tried Firefox and Opera). This is a lot of stuff and would need very time-consuming reading of the log-file.
Perhaps the next step is to bundle all entries coming from one domain?

---

### Post by mssever on 2007-09-13
> **xilix said:**
> All visited websites and their parts are listed (tried Firefox and Opera).
Yes, this should get most URLs regardless of the browser used (it even catches my weather applet). It doesn't get some Gmail stuff. My theory is that Gmail must use a nonstandard port number for some of its behind-the-scenes work.

> This is a lot of stuff and would need very time-consuming reading of the log-file.
Perhaps the next step is to bundle all entries coming from one domain?
Did you use the report program? ```
sudo net-responsibility-report | less
``` It does that already. Also, I've added in my not-yet-released development version the ability to exclude certain domain names from the reports.

---

### Post by xilix on 2007-09-14
No, I didn't use it. Looks very good. Perhaps later one can make a "tree-view" (like Nautilus-Folder-Tree) in the GUI. Then the accountability partner can choose on which domains he has to look closer...

If I have understood right, the ability to exclude certain domain names is a preference that the person who reads the reports can set. This would mean, that "secure" domains are not viewed in the report. That's a great feature, too. :)

Do you have already an idea how to transfer the reports to the accountability partner? Do you think it is possible via E-Mail?

---

### Post by xilix on 2007-09-14
I think I know how to start the mailing process periodically. I would suggest using anacron.
It's like cron, but it doesn't assume that the machine is running continuously. It not a real deamon, but it works like one. If your computer is turned off during the intended time to send the mail, this is performed at the next session. 
By default anacron can only start root-commands (which is only needed in this case, I think), but I also figured out how to start user-commands with it...

---

### Post by clmorg01 on 2007-09-14
I'll download and test it as well.  I'm looking forward to this.  :)

---

### Post by raijinsetsu on 2007-09-14
These log files can get pretty extensive. Have you thought about compressing them? or are they already compressed?
Also, could you use a backend such as MySQL, pySQL, etc?
If you used a backend to store the information, it could easily be read from anywhere on the local net.

---

### Post by clmorg01 on 2007-09-14
Doing the following command before any url request are in log will give the following error.


> sudo net-responsibility-report

> 
chris@chris-desktop:~/Projects/NetResponsiblity_Builds/net-responsibility-0.1$ sudo net-responsibility-report/usr/share/net-responsibility/lib/logfile.rb:169:in `list_dates': undefined method `sort!' for nil:NilClass (NoMethodError)
        from /usr/share/net-responsibility/lib/logfile.rb:39:in `initialize'
        from /usr/share/net-responsibility/lib/report.rb:32:in `new'
        from /usr/share/net-responsibility/lib/report.rb:32:in `initialize'
        from /usr/local/bin/net-responsibility-report:48:in `new'
        from /usr/local/bin/net-responsibility-report:48:in `main'
        from /usr/local/bin/net-responsibility-report:53



After I made some web request, it was fine.

-chris

---

### Post by mssever on 2007-09-14
> **xilix said:**
> No, I didn't use it. Looks very good. Perhaps later one can make a "tree-view" (like Nautilus-Folder-Tree) in the GUI. Then the accountability partner can choose on which domains he has to look closer...
That would be nice, but I don't think that it's possible in an e-mail. Eventually, I might experiment with using Javascript in an HTML mail message, but I suspect that a lot of mail readers disable Javascript.

It might actually be good to create a web service that the accountability partner can log in to have more control over the report. Anyone want to build that?

> If I have understood right, the ability to exclude certain domain names is a preference that the person who reads the reports can set. This would mean, that "secure" domains are not viewed in the report. That's a great feature, too. :)Actually, it's set on the machine being held accountable. It's not possible for the accountability partner to set it if the report is e-mailed. A web service would be good here, too.

I've thought a bit more about this feature now that you've mentioned it. I'm not sure that it's such a good idea, because it makes it trivial for the person being held accountable to cover his/her tracks. This needs to be re-thought. Should the report tool always generate full reports? Should it have a hard-coded exclude list that only covers stuff that (for example) Firefox downloads automatically? Or should it exclude based on some whitelist accessible from the Internet--assuming that a suitable list exists?

The underlying traffic capturing program, urlsnarf, doesn't grab SSL (secure) URLs. I haven't investigated why, but it likely is due to the encryption. I'm not sure whether this is a feature or a bug. :)

> **xilix said:**
> I think I know how to start the mailing process periodically. I would suggest using anacron.
Currently, the installer drops a symlink in /etc/cron.weekly, which is (I believe) run by anacron.

> **raijinsetsu said:**
> These log files can get pretty extensive. Have you thought about compressing them? or are they already compressed?
Also, could you use a backend such as MySQL, pySQL, etc?
If you used a backend to store the information, it could easily be read from anywhere on the local net.
Eventually, I'll probably change the logfile format to SQLite3. MySQL is too much unnecessary overhead. That should take care of compression, as well. My current format has turned out to be tricky to parse, and the report generating code is very fragile. Switching to SQLite3 should help immensely, together with the requisite rewrite of much of the the report code.

But this is a lower priority than getting some other stuff working. Oh, I also plan on including some logfile rotation eventually to ease up on the disk space.

> **clmorg01 said:**
> Doing the following command before any url request are in log will give the following error.
Thanks for the bug report. I believe that it's fixed now. I'll be releasing the next version soon.

---

### Post by mssever on 2007-09-14
I've just released version 0.2 (see the original post). Still no e-mail, though. :(

There's no direct upgrade path. Run the previous version's uninstall.sh script. (You can keep your logfile if you like; the config file has changed, so you should let the uninstaller delete your current config.) Then, extract the new version and run its install script.

---

### Post by xilix on 2007-09-14
> **mssever said:**
> That would be nice, but I don't think that it's possible in an e-mail. Eventually, I might experiment with using Javascript in an HTML mail message, but I suspect that a lot of mail readers disable Javascript.

It might actually be good to create a web service that the accountability partner can log in to have more control over the report. Anyone want to build that?
You're right, a web service would avoid a lot of problems. But I cannot do that. (I will continue testing and thinking...)

> **mssever said:**
> Actually, it's set on the machine being held accountable. It's not possible for the accountability partner to set it if the report is e-mailed. A web service would be good here, too.
I've thought a bit more about this feature now that you've mentioned it. I'm not sure that it's such a good idea, because it makes it trivial for the person being held accountable to cover his/her tracks. This needs to be re-thought. 
That was the intention of my question. I think this feature should be removed from the 'sending part'...
> **mssever said:**
> Should the report tool always generate full reports? Should it have a hard-coded exclude list that only covers stuff that (for example) Firefox downloads automatically? Or should it exclude based on some whitelist accessible from the Internet--assuming that a suitable list exists?
I think it's important (for the psychological part of the whole accountability process) that the accountable person knows that his/her partner will see all domains at first. The web service (or client software for the acc. partner) could be teachable and put several pages on a whitelist. Imagine the case when the accountable person discovers a website which is on the 'default whitelist' but has some questionable content. That would be a problem...

> **mssever said:**
> Currently, the installer drops a symlink in /etc/cron.weekly, which is (I believe) run by anacron.
That's correct. :-)

---

### Post by raijinsetsu on 2007-09-14
> **mssever said:**
> 
Eventually, I'll probably change the logfile format to SQLite3. MySQL is too much unnecessary overhead. That should take care of compression, as well. My current format has turned out to be tricky to parse, and the report generating code is very fragile. Switching to SQLite3 should help immensely, together with the requisite rewrite of much of the the report code.


If you're using SQL at all, then you can use PHP scripts so that the accountability partner could access, configure, and alter the logger and subsequent log files. This would avoid the e-mail system completely, and could probably be made more secure (tunneling the connection through SSH, etc.)
However, this is assuming that the client (watched) computer has web-services...

---

### Post by jonathonblake on 2007-09-14
> **mssever said:**
> I
 Still no e-mail, though. :(


Compress the files.
Convert to Mime.
then have elm send them, using the command line.
Or sendmail/qmail.

xan

jonathon

---

### Post by mssever on 2007-09-16
> **xilix said:**
> That was the intention of my question. I think this feature should be removed from the 'sending part'...

I think it's important (for the psychological part of the whole accountability process) that the accountable person knows that his/her partner will see all domains at first. The web service (or client software for the acc. partner) could be teachable and put several pages on a whitelist. Imagine the case when the accountable person discovers a website which is on the 'default whitelist' but has some questionable content. That would be a problem...I'll disable it. I want to get the next release out right away, though, so it'll wait until after the release (which will hopefully be today).

As far as the whitelist is concerned, you've raised a valid point. If the whitelist is good enough, it shouldn't be a concern. But, does such a list exist that's trustworthy? Probably not, at least over the long term. Spam blacklists have a tendency to go bad after a while, and such a whitelist would have the same vulnerability.
> **raijinsetsu said:**
> If you're using SQL at all, then you can use PHP scripts so that the accountability partner could access, configure, and alter the logger and subsequent log files. This would avoid the e-mail system completely, and could probably be made more secure (tunneling the connection through SSH, etc.)
However, this is assuming that the client (watched) computer has web-services...Running a web server on the accountable person's computer would be problematic. First, you have to properly configure it, and a generic configuration wouldn't necessarily be adequate. Then, you have to be able to reliably determine an IP address for the machine. Requiring the accountable person to set up something like DynDNS would be too complicated. And routers need to be properly configured, as well. Then you have the issue that many people turn off their computers and/or disconnect from the Internet when they're not in use.

My goal is to eventually have a program that requires no configuration other than some basic personal information and specifying who gets the reports.

The purpose of using SQL for the log files is twofold: First, it allows for simpler, more robust code. Second, it makes it take a bit more effort to manually purge undesirable information from the log, since you won't be able to simply fire up vi and delete at your whim.

> **jonathonblake said:**
> Compress the files.
Convert to Mime.
then have elm send them, using the command line.
Or sendmail/qmail.I'd rather generate a human-friendly report and send that than just sending the raw (optionally compressed) log.

Can elm send mail without a SMTP server? I'm guessing that most users won't have elm or mutt (or even mail) configured to use their regular e-mail.

I've just added SMTP support (it will be in release 0.3.0). It requires Postfix (or similar) to be installed. Then, Net Responsibility can e-mail the reports. Also, there's rudimentary support for using your regular e-mail SMTP settings.

This isn't really the behavior I want, since Postfix has to be configured. But, I don't know of a better, zero configuration, solution other than a web service which I don't yet have time to write.

---

### Post by mssever on 2007-09-16
Release 0.3.0 is here now--with e-mail! See the original post for instructions. Testers wanted.

---

### Post by xilix on 2007-09-16
> **mssever said:**
> My goal is to eventually have a program that requires no configuration other than some basic personal information and specifying who gets the reports.
...
I'd rather generate a human-friendly report and send that than just sending the raw (optionally compressed) log.
You're right. This is what we need.

I've installed v0.3.0 and I have the following output when typing  sudo net-responsibility-report
```
Debugger unavailable
/usr/share/net-responsibility/lib/report_mailer.rb:34:in `initialize': undefined method `smtp_server' for #<Options:0xb7c26dcc> (NoMethodError)
        from /usr/local/bin/net-responsibility-report:68:in `initialize'
        from /usr/local/bin/net-responsibility-report:75
```

The logfile itself works. I have installed Postfix and accepted the default settings in the configuration dialog.
Hope this is helpful...

---

### Post by mssever on 2007-09-17
> **xilix said:**
> I've installed v0.3.0 and I have the following output when typing  sudo net-responsibility-report
```
Debugger unavailable
/usr/share/net-responsibility/lib/report_mailer.rb:34:in `initialize': undefined method `smtp_server' for #<Options:0xb7c26dcc> (NoMethodError)
        from /usr/local/bin/net-responsibility-report:68:in `initialize'
        from /usr/local/bin/net-responsibility-report:75
```
I believe that you're getting this error because your config file is outdated. The config file in 0.3.0 contains an smtp_server section, which is necessary for sending mail. If you uninstall letting it remove your config file, then reinstall, it should work properly.

This is a bug, though, because the program should detect the problem and handle it in a friendlier way.

---

### Post by mssever on 2007-09-17
I've released version 0.3.1. You can find instructions in the original post. Be sure to uninstall any previous version before installing 0.3.1. There are no config file changes between 0.3.0 and 0.3.1, so if you're upgrading between those versions, you can keep your config file.

I'm looking for two specific kinds of testing: First, net-responsibility-daemon should start automatically during the system boot process. However, that's not working on my machine, and I want to know if it's working for anyone else. I don't know why it isn't working. Here's what you need to do: After rebooting, fire up a terminal and type ```
grep net-responsibility-daemon < /var/log/daemon.log | less
``` Look for messages similar to the following two lines (by the way, this won't work in releases earlier than 0.3.1):
```
Sep 17 15:54:25 scott-laptop /etc/init.d/net-responsibility-daemon: Starting net-responsibility-daemon
Sep 17 15:54:26 scott-laptop net-responsibility-daemon[6309]: Starting
```Do you see both lines, or only the first one? The absence of the second line means that net-responsibility-daemon isn't actually running and is therefore not monitoring your network activity. You can manually start it with ```
sudo net-responsibility-daemon
``` but it's supposed to start automatically.

The second thing I want to know is about how long net-responsibility-report takes to generate a report after you have a day or two worth of logged data.

By the way, xilix, thanks for all the testing you've done so far.

---

### Post by xilix on 2007-09-18
> **mssever said:**
> Do you see both lines, or only the first one? The absence of the second line means that net-responsibility-daemon isn't actually running and is therefore not monitoring your network activity. 

I see both lines :-) :

```
Sep 18 11:55:05 SNB /etc/init.d/net-responsibility-daemon: Starting net-responsibility-daemon
Sep 18 11:55:05 SNB net-responsibility-daemon[4899]: Starting
```

> **mssever said:**
> The second thing I want to know is about how long net-responsibility-report takes to generate a report after you have a day or two worth of logged data.

How can I see this best? I'm not sure, if my postfix-configuration is correct.

---

### Post by mssever on 2007-09-18
> **xilix said:**
> I see both lines :-) :Good. After I posted that question, I was able to track down that bug. The fact that you got both lines confirms my solution, because that particular bug shouldn't have affected you in the first place.
> How can I see this best? I'm not sure, if my postfix-configuration is correct.Provided that you've put an e-mail address of yours in the email_to section of the config file and set use_smtp to true, running the report tool should send you an email. If you get the e-mail, then postfix is adequately configured. (I'm really not a postfix expert.) If you get a text dump of the report, or if you get no email, you can look in /var/log/syslog for clues.

One way to time the report program is this: [code]sudo -v && time sudo net-responsibility-report[code]

Edit: By the way, regardless of whether your postfix configuration is correct, your timing results shouldn't be too different. Sending the e-mail only takes a small percentage of the overall time.

---

### Post by xilix on 2007-09-18
OK, the result to 

```
sudo -v && time sudo net-responsibility-report
```

is

```
...
real    1m10.071s
user    1m1.880s
sys     0m7.324s
```

Is this the time you want?

I have an AMD Turion 64 X2 DualCore Processor with 2GB RAM. Both Cores stay at 800 MHz and the CPU-Usage is about 50 % during the calculation. The logfile is 456,8 kByte. Hope this helps...

---

### Post by mssever on 2007-09-18
That's what I wanted. But the time was longer than what I'd hoped for. I guess I'll need to do some serious optimization there. I had suspected as much, but I was hoping that I was wrong. Your computer is much faster than mine, yet it still took over a minute.

---

### Post by mssever on 2007-09-20
I've just released Net Responsibility 0.3.2. New in this release is a better configuration program for the installer. It uses a library that I added that will be useful also for debconf and the GUI. (But the GUI is on hold for now. I'm quite inexperienced with GUI programming and have a lot to learn. Right now I think my time would be better spent on other areas of the program.)

Please test the installer. To run just the configurator (for testing purposes), type ```
sudo net-responsibility-config-cli
```

As always, be sure to uninstall the previous version before installing this one. You can keep your config and log files if you like.

---

### Post by xilix on 2007-09-22
Hey great! :) congratulations!

This time the installation was super-easy! And the sending of the report worked! Thank you very much.

I'm looking forward to further improvements. 

You said, that you are not experienced in making GUIs. Well, me too. But I think Glade is very easy to use. It produces an XML-file. I think libglade or something like that renders Gtk+-GUIs. I would like playing around with Glade, but I don't know anything about the 'Ruby-Gtk-Bindings'...

Can anyone else help out?

---

### Post by mssever on 2007-09-22
> **xilix said:**
> You said, that you are not experienced in making GUIs. Well, me too. But I think Glade is very easy to use. It produces an XML-file. I think libglade or something like that renders Gtk+-GUIs. I would like playing around with Glade, but I don't know anything about the 'Ruby-Gtk-Bindings'...
If you're interested in playing around with Glade, I've got a Glade file under src/gui/net-responsibility-config-gui.glade that could use another set of eyes. I couldn't figure out how to make it word wrap the labels. If you like playing around with Glade, you might be able to figure that out... Also, Glade doesn't seem to like using the icons I designed.

There's one other thing I need confirmation on. I've been working on rewriting the logging part to use SQLite3. Unfortunately, I've been getting a crash that's pretty much a show stopper. I'm pretty sure that it's a bug in Ruby's SQLite3 driver, not my code. Before I contact the Ruby mailing list, I'd like some confirmation of the bug. I'm attaching the current development snapshot. (I'm not making a release because the code is only partially converted to the new system and so is in a non-working state.)[LIST=1]
[*]Install libsqlite3-ruby
[*]Make a backup of your log file if you want to keep it
[*]Uninstall your current Net Responsibility, deleting your log file
[*]Install the new (broken) code
[*]Type ```
sudo net-responsibility-daemon -d
```Unless you include the -d switch, you won't see the crash.
[*]Do you get a message like this? ```
/usr/lib/ruby/1.8/sqlite3/driver/native/driver.rb:108: [BUG] Segmentation fault
ruby 1.8.5 (2006-08-25) [i486-linux]

Aborted (core dumped)
```[/LIST]If this crash can't be resolved, I'll have to hunt for a log format plan C. :(

By the way, I'm running standard Ubuntu Feisty (not CE). What about you?

---

### Post by xilix on 2007-09-23
> **mssever said:**
> If you're interested in playing around with Glade, I've got a Glade file under src/gui/net-responsibility-config-gui.glade that could use another set of eyes. I couldn't figure out how to make it word wrap the labels. If you like playing around with Glade, you might be able to figure that out... Also, Glade doesn't seem to like using the icons I designed.

Hm. Do you use Glade 2 or Glade 3? I've installed both and can make word-wraps in the labels very easily with both in the Properties editor. Another way is setting the width of the label. But I guess that's not the recommended way.

What filetypes are your icons?

> **mssever said:**
> Do you get a message like this?

Yes. Here is my output
```
Starting in the foreground killed a Net Responsibility daemon.
When this instance exits, no daemon will be running.
net-responsibility-daemon[8311]: Starting
/usr/lib/ruby/1.8/sqlite3/driver/native/driver.rb:108: [BUG] Segmentation fault
ruby 1.8.4 (2005-12-24) [i486-linux]

Aborted (core dumped)
```

> **mssever said:**
> By the way, I'm running standard Ubuntu Feisty (not CE). What about you?

I'm running the Ubuntu CE version (still Edgy)...

---

### Post by mssever on 2007-09-23
> **xilix said:**
> Hm. Do you use Glade 2 or Glade 3? I've installed both and can make word-wraps in the labels very easily with both in the Properties editor. Another way is setting the width of the label. But I guess that's not the recommended way.I'm using Glade 2.12.1, which I got from the repos. Given that the Feisty version of Gnome is 2.18, I wonder if the repo version of Glade is outdated. 

When it comes to word wrap, apparently I've been doing something wrong; I haven't found such an option anywhere. If you could fix it, I'd appreciate it.

> What filetypes are your icons?PNG (with SVG masters). I might have sorted out that problem. I initially designed the interface before I designed the icons, so I used stock icons. Later, I switched to my icons. When I told Glade to generate C source (so I could test; my only options were C, C++ and Ada), I compiled and ran the resulting code, which used the stock icons instead of mine. I finally ended up hand hacking Glade's XML file since Glade wasn't writing it properly.


> 
Yes. Here is my output
According to the folks on #ruby-lang, the Ruby's sqlite3 library is quite buggy. A debian user there also confirmed this bug. I've managed to work around that bug, but now I'm getting bitten by another. I'm still trying to figure that out, but if anyone else has any alternatives, I'm listening...

EDIT: Yay! I think I solved it! I had a syntax error in my query that Ruby's lib didn't properly diagnose. I installed the CLI sqlite3 program and was able to debug my SQL from there. SQLite3 certainly behaves a bit differently from MySQL. I'm finished for tonight, but if all goes well I should be able to release 0.4.0 soon. Then, I'll be able to work on the GUI and develop a deb package. At that point, Net Responsibility will have most of the minimum requisite features for a real Internet accountability program.

---

### Post by xilix on 2007-09-24
> **mssever said:**
> When it comes to word wrap, apparently I've been doing something wrong; I haven't found such an option anywhere. If you could fix it, I'd appreciate it.

Since I am no developer I have to read some documentation about SVN before I can access the SVN repository of the SourceForge.net project. I don't know how long this takes...

But I've looked into the modified glade-file. I think you can just insert a line-break in the text of the label. If you're hacking the xml-files anyway this should be the fastest solution for the moment...

... looking forward to a deb-package :-)

---

### Post by mssever on 2007-09-24
> **xilix said:**
> Since I am no developer I have to read some documentation about SVN before I can access the SVN repository of the SourceForge.net project. I don't know how long this takes...
Assuming that you have the subversion package installed, you can do the following:```
svn checkout https://responsibility.svn.sourceforge.net/svnroot/responsibility/trunk net-responsibility-svn
```That will get you a copy and put it in a directory called net-responsibility-svn. Later, I think that you can cd into that dir and type ```
svn update
```to get any changes to svn. I'm not positive about that, though. I'm pretty much an SVN novice.
> But I've looked into the modified glade-file. I think you can just insert a line-break in the text of the label. If you're hacking the xml-files anyway this should be the fastest solution for the moment...Yes, that would be the fastest solution, and it's one I've already experimented with. Maybe it's my web development background coming through, but I wince at the thought of hard-coded line breaks. What if the user resizes the window? The labels should automatically wrap themselves. But maybe that's not appropriate thinking for GTK?

---

### Post by mssever on 2007-09-24
I've just released version 0.4.0. The biggest change is in the log file format. It's MUCH faster now, and a lot easier to maintain. This means that some testing of net-responsibility-report is in order to verify that I fixed everything I broke. :)

Also, there should be a couple of menu entries for the configurator. Please verify that they're there and have icons. They're in Applications > System Tools and Applications > Networking. Both entries do the same thing.

---

### Post by xilix on 2007-09-25
Can you show me how to uninstall the broken version first?

Thank you!

---

### Post by mssever on 2007-09-25
You can cd to your broken version source directory and run sudo ./uninstall. Failing that, the uninstaller in the new version should do a pretty good job of cleaning up. You might get a couple of error messages when installing the new version, but nothing serious.

---

### Post by xilix on 2007-09-25
Both uninstallers get this output

```
sudo ./uninstall 
Password:
Are you sure you want to uninstall Net Responsibility? [y/N] y
 * Stopping the Net Responsibility daemon net-responsibility-daemon             /etc/init.d/net-responsibility-daemon: Stopping net-responsibility-daemon
kill: 69: No such process

                                                                         [fail]
Unable to stop the Net Responsibility daemon. Aborting.
```

So I thougt maybe I don't have to uninstall it and installed the new version (0.4.0). The installation seemed to work but I get this error, when I try to generate a report...
```
sudo net-responsibility-report
/usr/lib/ruby/1.8/sqlite3/errors.rb:94:in `check': no such column: date (SQLite3::SQLException)
        from /usr/lib/ruby/1.8/sqlite3/statement.rb:70:in `initialize'
        from /usr/lib/ruby/1.8/sqlite3/database.rb:183:in `prepare'
        from /usr/lib/ruby/1.8/sqlite3/database.rb:274:in `query'
        from /usr/share/net-responsibility/lib/modules/db.rb:93:in `get_dates'
        from /usr/share/net-responsibility/lib/report.rb:38:in `initialize'
        from /usr/local/bin/net-responsibility-report:75:in `initialize'
        from /usr/local/bin/net-responsibility-report:87
```

---

### Post by mssever on 2007-09-25
I forgot about that error in the broken version. You'll need to do a manual uninstall:[LIST=1]
[*]Stop the daemon: ```
sudo killall net-responsibility-daemon
```
[*]Delete the files: ```
sudo rm -r /etc/init.d/net-responsibility-daemon /usr/share/net-responsibility
```
[*]Rename your log file (or delete it): ```
sudo mv /var/log/net-responsibility.log /var/log/net-responsibility.log.old
```
[*]Run the installer. You'll see some errors about files already existing, but don't worry about them.[/LIST]That should fix it.

By the way, the error you got is because the old log file is incompatible with the new one.

---

### Post by jonathonblake on 2007-09-25
[QUOTE=xilix]
All visited websites and their parts are listed (tried Firefox and Opera).
[/QUOTE]

Quick questions:

* Does it track torrent connections?
* Does it track IRC connections;
* Does it track usenet connections;

If it doesn't, adding that capability might be useful.  

xan

jonathon

---

### Post by mssever on 2007-09-26
> **jonathonblake said:**
> * Does it track torrent connections?
If the .torrent file is downloaded by HTTP, which is likely, then it logs that. But I don't think that it logs the actual torrent.
> Does it track IRC connections;No.
> Does it track usenet connections;No.

It also doesn't seem to log secure websites, which is, in my opinion, the biggest hole.

Those features would definitely be nice to have, but I don't know right now how to get at that data. If someone can contribute that, it would be great. Otherwise, I'll add those features as I have time to do research. Right now, I'm trying to get all the basic features working.

---

### Post by xilix on 2007-09-26
> **mssever said:**
> I've just released version 0.4.0. The biggest change is in the log file format. It's MUCH faster now, and a lot easier to maintain. This means that some testing of net-responsibility-report is in order to verify that I fixed everything I broke. :)

Also, there should be a couple of menu entries for the configurator. Please verify that they're there and have icons. They're in Applications > System Tools and Applications > Networking. Both entries do the same thing.

OK, now everything tested and working. :-) It's really MUCH faster...

---

### Post by merval on 2007-09-27
I just wanted to say that I found this thread and within 5 minutes has the whole thing installed and working and sent out a report. The report hit my yahoo email instantly.

Bravo! 

This is a very good piece of software! Keep me up to date on the version updates and i will test everything you add.

Thanks!!

- Dan

---

### Post by mssever on 2007-09-27
> **merval said:**
> I just wanted to say that I found this thread and within 5 minutes has the whole thing installed and working and sent out a report. The report hit my yahoo email instantly.

Bravo! 

This is a very good piece of software! Keep me up to date on the version updates and i will test everything you add.

Thanks!!

- Dan
Thanks, Dan! I post in this thread every time I release a new version, so as long as you're subscribed here, you'll get notified.

---

### Post by mssever on 2007-10-01
I've just released Net Responsibility 0.4.1. New this time around is that there is a .deb file. Be sure to uninstall any previous version before installing the .deb. Please verify that the .deb works for you. I already know that it doesn't handle configuration properly; that's something I'm still working on.

---

### Post by xilix on 2007-10-02
> **mssever said:**
> I've just released Net Responsibility 0.4.1. New this time around is that there is a .deb file. Be sure to uninstall any previous version before installing the .deb. Please verify that the .deb works for you. I already know that it doesn't handle configuration properly; that's something I'm still working on.

I've installed v0.4.1. During the installation it asked whether I want to install the version of the maintainer or not. I decided to take the version of the maintainer (Y). Probably it deleted my old conf-file. When I try to generate a report it generates something but it doesn't send the report. I guess that it's the conf-issue you already know...

---

### Post by mssever on 2007-10-02
Yes, you probably hosed your configuration. I find deb packaging to be very complicated, and I don't understand it very well. But, I don't think that you'll see that message again, and new users definitely won't see it.

Try going to Applications > Internet > Configure Net Responsibility and go through the configuration. See if that fixes the report tool.

---

### Post by xilix on 2007-10-04
No, it still doesn't work...
```
$ sudo net-responsibility-report
net-responsibility-report[30758]: Generating report
/usr/lib/ruby/1.8/sqlite3/errors.rb:94:in `check': Unable to close due to unfinalised statements (SQLite3::BusyException)
        from /usr/lib/ruby/1.8/sqlite3/database.rb:153:in `close'
        from /usr/local/bin/net-responsibility-report:84:in `initialize'
        from /usr/local/bin/net-responsibility-report:90
```

---

### Post by grendelkhan on 2007-10-04
Any idea when this will be ready for Gutsy?  They've changed the name of libdemonize-ruby so I can't get the deb to install.

---

### Post by mssever on 2007-10-07
> **xilix said:**
> No, it still doesn't work...
```
$ sudo net-responsibility-report
net-responsibility-report[30758]: Generating report
/usr/lib/ruby/1.8/sqlite3/errors.rb:94:in `check': Unable to close due to unfinalised statements (SQLite3::BusyException)
        from /usr/lib/ruby/1.8/sqlite3/database.rb:153:in `close'
        from /usr/local/bin/net-responsibility-report:84:in `initialize'
        from /usr/local/bin/net-responsibility-report:90
```
Hmm... Do you keep getting that error if you try several times?
> **grendelkhan said:**
> Any idea when this will be ready for Gutsy?  They've changed the name of libdemonize-ruby so I can't get the deb to install.

Thanks for telling me about this. I'm still running Feisty. libdaemonize-ruby has been removed from Debian--and thus from Ubuntu. Supposedly, libdaemons-ruby provides backward compatibility. I've released 0.4.2 with revised dependencies. Let me know if it works.

---

### Post by xilix on 2007-10-08
> **mssever said:**
> Hmm... Do you keep getting that error if you try several times?

No. The second time it works....

---

### Post by nitep on 2007-10-13
Hi look at my tutorial [http://ubuntuforums.org/showthread.php?t=566698](http://ubuntuforums.org/showthread.php?t=566698)
You can set it to record stats of all sites visited and give the account username and password for someone else to see the stats. Also see [http://nbcf.witnesstoday.org/links.html#safe](http://nbcf.witnesstoday.org/links.html#safe)
Regards
Peter

---

### Post by bsalt on 2007-10-13
Hey! Thanks for this app! I am wondering though... I have a Gmail account. Is there a way I can specify a name and password for sending mail through Gmail (smtp.gmail.com)?

---

### Post by eric.duveau on 2007-10-16
Very interesting, I hope It will be ready very soon

---

### Post by grendelkhan on 2007-10-16
> **bsalt said:**
> Hey! Thanks for this app! I am wondering though... I have a Gmail account. Is there a way I can specify a name and password for sending mail through Gmail (smtp.gmail.com)?

Ditto, I've installed it on Gutsy, now I just need this to make it complete.

Thanks a million for developing this, I've been looking for something like this on Linux for ages!

---

### Post by bsalt on 2007-10-17
I hear ya. This is somewhat comparable to the program X3Watch, but for Linux. It really is a nice app.

---

### Post by eric.duveau on 2007-10-19
The following link is another solution. It is described step by step. It shows how to sends CEubuntu dansguardian log by email.

[http://forums.churchforge.net/viewtopic.php?t=330](http://forums.churchforge.net/viewtopic.php?t=330)

---

### Post by grnqrtr on 2007-10-19
When I enter "sudo net-responsibility-report" in a terminal I get an error:

<code>
net-responsibility-report[6265]: Generating report
net-responsibility-report[6265]: Sending report
/usr/lib/ruby/1.8/net/protocol.rb:206:in `initialize': Connection refused - connect(2) (Errno::ECONNREFUSED)
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `new'
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `old_open'
        from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
        from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `old_open'
        from /usr/lib/ruby/1.8/net/smtp.rb:393:in `do_start'
        from /usr/lib/ruby/1.8/net/smtp.rb:378:in `start'
        from /usr/lib/ruby/1.8/net/smtp.rb:316:in `start'
        from /usr/share/net-responsibility/lib/report_mailer.rb:76:in `send_message'
        from /usr/share/net-responsibility/lib/report_mailer.rb:97:in `create_and_send'
        from /usr/local/bin/net-responsibility-report:86:in `initialize'
        from /usr/local/bin/net-responsibility-report:90:in `new'
        from /usr/local/bin/net-responsibility-report:90
</code>



Does anyone know how I can fix this "Connection refused" error problem?

---

### Post by leetcharmer on 2007-10-20
Where are the debs for this so I can install it with Gutsy? :D

---

### Post by grendelkhan on 2007-10-21
Grab the tar file on the first page, it creates debs you can install.

---

### Post by leetcharmer on 2007-10-21
Alright, it's installed now, and configured ... how do I test to see if the e-mails are being sent correctly.  I'm not sure if it is because the smtp address I use for outgoing mail requires authentication.

How do I send some test mails?

Here's the latest info for gmail (that's what I want to use):
>       Google Gmail Outgoing Mail Server (SMTP): smtp.gmail.com

      The Gmail SMTP server requires authentication (use the same settings as for the incoming mail server)

      The Google Gmail SMTP Server requires an encrypted connection (SSL) on port 465.

---

### Post by leetcharmer on 2007-10-22
I also get errors when running net-responsibility-report:

```
net-responsibility-report[20423]: Generating report
/usr/lib/ruby/1.8/sqlite3/errors.rb:94:in `check': Unable to close due to unfinalised statements (SQLite3::BusyException)
        from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in `close'
        from /usr/local/bin/net-responsibility-report:84:in `initialize'
        from /usr/local/bin/net-responsibility-report:90:in `new'
        from /usr/local/bin/net-responsibility-report:90
```

Ideas?

---

### Post by mssever on 2007-10-25
Developing this program meant that I somewhat checked out of real life for a while. To compensate, I took a (somewhat unintended) breather from work on Net Responsibility. I'm back, now, and I'll see if I can shed some light on the discussions that I missed.

Also, I've got log rotation nearly complete. Unrotated logs can cause net-responsibility-report to run really slowly.
> **nitep said:**
> Hi look at my tutorial [http://ubuntuforums.org/showthread.php?t=566698](http://ubuntuforums.org/showthread.php?t=566698)
You can set it to record stats of all sites visited and give the account username and password for someone else to see the stats. Also see [http://nbcf.witnesstoday.org/links.html#safe](http://nbcf.witnesstoday.org/links.html#safe)
Regards
Peter
OpenDNS is a valuable tool. Thanks for mentioning it. However, internet accountability software is a bit different from filtering programs. I use OpenDNS myself, but all filters can be circumvented. Internet accountability software can be circumvented, but if you do so, it will be evident. (Net Responsibility isn't perfect in this area yet.)
> **bsalt said:**
> Hey! Thanks for this app! I am wondering though... I have a Gmail account. Is there a way I can specify a name and password for sending mail through Gmail (smtp.gmail.com)?
I wish I knew how to make that happen. If you read the earlier posts on this thread (and I don't blame you if you didn't), you would notice that Net Responsibility went for quite some time without email because I couldn't find a workable way to connect to Gmail. The current workaround of using Postfix is ugly, but it works. Until I can figure something better out, you won't be able to send via Gmail.

NOTE: You don't have to send through Gmail to be able to use your Gmail address on the From: line of the e-mails.
> **eric.duveau said:**
> The following link is another solution. It is described step by step. It shows how to sends CEubuntu dansguardian log by email.

[http://forums.churchforge.net/viewtopic.php?t=330](http://forums.churchforge.net/viewtopic.php?t=330)
Hmm... That link's dead. I'm interested in seeing it, though.
> **grnqrtr said:**
> When I enter "sudo net-responsibility-report" in a terminal I get an error:

<code>
net-responsibility-report[6265]: Generating report
net-responsibility-report[6265]: Sending report
/usr/lib/ruby/1.8/net/protocol.rb:206:in `initialize': Connection refused - connect(2) (Errno::ECONNREFUSED)
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `new'
        
Hmm... I've never seen that error before. I wonder if Postfix is misconfigured? See if this command is able to send email: ```
echo "Test message" | mail -s "Test subject" your@email.com
```> **leetcharmer said:**
> Alright, it's installed now, and configured ... how do I test to see if the e-mails are being sent correctly.  I'm not sure if it is because the smtp address I use for outgoing mail requires authentication.You can test whether it's sending mail properly by adding your email address to the list of email recipients. Go to Applications > Internet > Configure Net Responsibility and set it there.

About Gmail, see my reply earlier in this post.> **leetcharmer said:**
> I also get errors when running net-responsibility-report:

```
net-responsibility-report[20423]: Generating report
/usr/lib/ruby/1.8/sqlite3/errors.rb:94:in `check': Unable to close due to unfinalised statements (SQLite3::BusyException)
        from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in `close'
        from /usr/local/bin/net-responsibility-report:84:in `initialize'
        from /usr/local/bin/net-responsibility-report:90:in `new'
        from /usr/local/bin/net-responsibility-report:90
```Ideas?
That's a known bug, but I haven't yet figured out how to fix it. It's really annoying, though, because the error you're seeing is a minor bug, but the fact that it isn't sending mail is evidence of a more serious problem. Unfortunately, the BusyException you're seeing has replaced the more valuable error message. Grr. Maybe I'll just silence the BusyException in the future.

Just now thought of something. I'm putting it here to remind myself: I could still print the BusyException without re-raising it. That way, errors wouldn't go unreported.

---

### Post by eric.duveau on 2007-10-25
I think there is a problem on the server. Yet, I have succeeded to browse with konqueror and opera.

For those who prefer, I have zipped it as an attached file

 > Originally Posted by eric.duveau  View Post
The following link is another solution. It is described step by step. It shows how to sends CEubuntu dansguardian log by email.

[http://forums.churchforge.net/viewtopic.php?t=330](http://forums.churchforge.net/viewtopic.php?t=330)

---

### Post by mssever on 2007-10-26
After a hiatus, I've released Net Responsibility 0.4.3. Instructions on how to get it are in the original post. There are two major changes of interest to normal users:[LIST=1]
[*]Logfile rotation. This is a long-overdue feature. Now, when you run the report tool, all logfile entries that were included in the report are purged from the logfile. If you want to maintain a record, add your email address to the list of send to addresses in the configuration.
[*]Major performance improvement. I've changed the way the report tool handles its data for a major speed improvement. On my older laptop, the time to process a very large logfile (several weeks' worth of data) went from several hours to under 30 seconds. I'd be very interested to see other people's results. (Note: comparisons are only meaningful if you're currently running a 0.4.x release.)[LIST=1]
[*]Make a note of the size of /var/log/net-responsibility.log
[*]Run ```
sudo -v; time sudo net-responsibility-report
``` and note the time used.
[*]Upgrade to 0.4.3 and re-run the report using the command above.
[*]Post the data you collected.[/LIST] [/LIST]I'd like testers to verify a few things:[LIST=1]
[*]Verify that the report tool still works and that the daemon doesn't die as a result of running the report. You can use ```
ps -ef | grep net-responsibility-daemon
``` Both before and after running the report to verify that. If the daemon dies as a result of running the report, please post the output of both of the following commands: ```
cat /var/log/daemon.log | grep net-responsibility
cat /var/log/syslog | grep net-responsibility
```
[*]If you DON'T encounter the bug documented at the end of the original post, I'd like to hear about it.
[*]If you encounter any other problems, do tell.[/LIST]

---

### Post by grnqrtr on 2007-10-27
I installed 0.4.3 over 0.4.2 because I couldn't find an "uninstall.sh" file anywhere.  Will that be okay or do I need to uninstall the right way?  If I need to uninstall the old one then where is the uninstall.sh file?

Thanks

---

### Post by mssever on 2007-10-28
> **grnqrtr said:**
> I installed 0.4.3 over 0.4.2 because I couldn't find an "uninstall.sh" file anywhere.  Will that be okay or do I need to uninstall the right way?  If I need to uninstall the old one then where is the uninstall.sh file?

Thanks

The uninstall file hasn't existed since 0.4.0--now the .deb file is the way to install and upgrade. If you have 0.4.2, presumably you installed the .deb, in which case you can just install the new .deb.

Where did you find those directions? It sounds like I might have missed an update.

---

### Post by grnqrtr on 2007-10-28
> Where did you find those directions? It sounds like I might have missed an update.

I saw the instructions earlier in this thread about uninstalling, but that must have been for the older version.  I must have missed where it said an uninstall.sh wasn't needed after 0.4.0.  Thank you.

---

### Post by leetcharmer on 2007-10-30
how long should it generally take for a report to be generated after typing in: $ sudo net-responsibility-report in 0.4.3?  It sure is taking a long time.

---

### Post by leetcharmer on 2007-10-30
```
simbala@gerbert:~$ sudo net-responsibility-report
net-responsibility-report[6754]: Generating report
net-responsibility-report[6754]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[6754]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[6754]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[6754]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[6754]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[6754]: => from /usr/local/bin/net-responsibility-report:116
/usr/lib/ruby/1.8/sqlite3/resultset.rb:140:in `next': Interrupt
        from /usr/lib/ruby/1.8/sqlite3/resultset.rb:161:in `each'
        from /usr/share/net-responsibility/lib/modules/db.rb:220:in `get_paths'
        from /usr/share/net-responsibility/lib/report.rb:57:in `url_report'
        from /usr/share/net-responsibility/lib/report.rb:55:in `each'
        from /usr/share/net-responsibility/lib/report.rb:55:in `url_report'
        from /usr/share/net-responsibility/lib/report.rb:46:in `each'
        from /usr/share/net-responsibility/lib/report.rb:46:in `url_report'
        from /usr/share/net-responsibility/lib/report.rb:92:in `full_report'
        from /usr/local/bin/net-responsibility-report:86:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116
```

---

### Post by leetcharmer on 2007-10-30
Nevermind.  Let it generate overnight.  Here's the results.

```
simbala@gerbert:~$ sudo -v; time sudo net-responsibility-report
net-responsibility-report[6785]: Generating report
net-responsibility-report[6785]: Sending report
net-responsibility-report[6785]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[6785]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[6785]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[6785]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[6785]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[6785]: => from /usr/local/bin/net-responsibility-report:116
/usr/lib/ruby/1.8/net/protocol.rb:206:in `initialize': getaddrinfo: Name or service not known (SocketError)
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `new'
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `old_open'
        from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
        from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `old_open'
        from /usr/lib/ruby/1.8/net/smtp.rb:393:in `do_start'
        from /usr/lib/ruby/1.8/net/smtp.rb:378:in `start'
        from /usr/lib/ruby/1.8/net/smtp.rb:316:in `start'
        from /usr/share/net-responsibility/lib/report_mailer.rb:76:in `send_message'
        from /usr/share/net-responsibility/lib/report_mailer.rb:97:in `create_and_send'
        from /usr/local/bin/net-responsibility-report:87:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116

real    4m33.802s
user    2m59.551s
sys     1m29.530s

```

Do you perhaps know of a free smtp server with no authentication?

---

### Post by mssever on 2007-10-30
> **leetcharmer said:**
> how long should it generally take for a report to be generated after typing in: $ sudo net-responsibility-report in 0.4.3?  It sure is taking a long time.
It depends on how fast your machine is, how much memory you have, and how big your logfile is. I'd be interested in finding out the logfile size to comparre it with the times you got below. The logfile is /var/log/net-responsibility.log
> **leetcharmer said:**
> ```
simbala@gerbert:~$ sudo -v; time sudo net-responsibility-report
<snip>
/usr/lib/ruby/1.8/net/protocol.rb:206:in `initialize': getaddrinfo: Name or service not known (SocketError)
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `new'
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `old_open'
        from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
        from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `old_open'
        from /usr/lib/ruby/1.8/net/smtp.rb:393:in `do_start'
        from /usr/lib/ruby/1.8/net/smtp.rb:378:in `start'
        from /usr/lib/ruby/1.8/net/smtp.rb:316:in `start'
        from /usr/share/net-responsibility/lib/report_mailer.rb:76:in `send_message'
        from /usr/share/net-responsibility/lib/report_mailer.rb:97:in `create_and_send'
        from /usr/local/bin/net-responsibility-report:87:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116

real    4m33.802s
user    2m59.551s
sys     1m29.530s

```
My best guess is that this error is the result of Postfix being misconfigured. Please try this: ```
echo "Test message" | mail -s "Test subject" your@email.com
```Let me know whether the email goes through or not.

There are two reasons why I'm asking for this: First, I want to get Net Responsibility working for you. Second, the fact that you saw such an error message proves that there's another bug in my program, and I want to be able to reproduce it so I can fix it. In this case, if my guess is right, I don't think that I can prevent this error from occurring (since I can't control Postfix's configuration), but the program should at the minimum report an error that is understandable by non-programmers and gives an indication of what to do to fix it.
> Do you perhaps know of a free smtp server with no authentication?A remote server? No. Most ISPs shut down those kinds of servers as soon as they find them because spammers love to use them to send spam. And such a server wouldn't help your problem, anyway, because currently Net Responsibility can't connect to a remote SMTP server. In the next release, I plan to adjust the dependencies so that you can use most MTAs (mail transport agents, such as postfix or exim4).

---

### Post by grnqrtr on 2007-11-01
I am running the newest version, 0.4.3, and I have a couple problems:

> Now, when you run the report tool, all logfile entries that were included in the report are purged from the logfile.
This feature doesn't seem to be working because each time I run "sudo net-responsibility-report" I still have all the old reports in the email I get.

The second problem is that it doesn't seem to send the report to some emails that are in my configuration file.  I have confirmed getting emails from *@yahoo.co.jp and *@gmail.com, but both times that I have sent to *@hotmail.com, the message isn't recieved.

And both of the people that are helping me keep accountable have hotmail email addresses, so I hope someone can help me.

Thank you.

---

### Post by mssever on 2007-11-02
> **grnqrtr said:**
> This feature doesn't seem to be working because each time I run "sudo net-responsibility-report" I still have all the old reports in the email I get.So you're saying that your logs aren't getting purged? Sounds like I need to enable some additional debugging info so I can find out why your logs aren't getting purged. Are you getting any error messages? Actually, please post the output of ```
sudo net-responsibility-report
```

> The second problem is that it doesn't seem to send the report to some emails that are in my configuration file.  I have confirmed getting emails from *@yahoo.co.jp and *@gmail.com, but both times that I have sent to *@hotmail.com, the message isn't recieved.Have you checked the spam folder in hotmail? My first guess is that hotmail thinks that the report is spam.

---

### Post by leetcharmer on 2007-11-02
> **mssever said:**
> My best guess is that this error is the result of Postfix being misconfigured. Please try this: ```
echo "Test message" | mail -s "Test subject" your@email.com
```Let me know whether the email goes through or not.

$ echo "Test message" | mail -s "Test subject" [email]JohnnyJIV [at] gmail [dot] com[/email]
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 75

---

### Post by mssever on 2007-11-02
> **leetcharmer said:**
> $ echo "Test message" | mail -s "Test subject" JohnnyJIV [at] gmail [dot] com
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 75

Yes, postfix is misconfigured. Run ```
sudo dpkg-reconfigure postfix
``` You should be able to pretty much accept the defaults. Here's a screen-by-screen run through (I'm running Feisty; it might be different in other versions):[LIST]
[*]Choose Internet site on the first screen
[*]Choose (or accept) your machine's mail name. e.g., I use scott-laptop.mss
[*]Enter your system username
[*]Don't worry too much about the next screen since you won't be receiving mail directly
[*]Choose No
[*]Enter 127.0.0.0/8
[*]For the rest of the options, you can just accept the default.[/LIST]After reconfiguring, try running the test I gave you again.

---

### Post by grnqrtr on 2007-11-02
> So you're saying that your logs aren't getting purged? Sounds like I need to enable some additional debugging info so I can find out why your logs aren't getting purged. Are you getting any error messages? Actually, please post the output of "sudo net-responsibility-report"

Here it is:
```
grnqrtr@grnqrtr-laptop:~$ sudo net-responsibility-report
net-responsibility-report[26871]: Generating report
net-responsibility-report[26871]: Sending report
net-responsibility-report[26871]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[26871]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[26871]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[26871]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[26871]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[26871]: => from /usr/local/bin/net-responsibility-report:116
/usr/share/net-responsibility/lib/modules/db.rb:160:in `rotate_log': undefined method `close' for nil:NilClass (NoMethodError)
        from /usr/share/net-responsibility/lib/modules/db.rb:149:in `each'
        from /usr/share/net-responsibility/lib/modules/db.rb:149:in `rotate_log'
        from /usr/local/bin/net-responsibility-report:97:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116

```

I also checked to see if the report was going into the Junk folder of the hotmail account that I was trying to send it to and it wasn't in there, so I don't know what is going on with that.  It sends fine to all the other emails.

---

### Post by leetcharmer on 2007-11-04
How long should it take to go through?

> $ echo "Test message" | mail -s "Test subject" JohnnyJIV [at] gmail [dot] com

got no errors

---

### Post by mssever on 2007-11-07
> **grnqrtr said:**
> Here it is:
```
/usr/share/net-responsibility/lib/modules/db.rb:160:in `rotate_log': undefined method `close' for nil:NilClass (NoMethodError)
        from /usr/share/net-responsibility/lib/modules/db.rb:149:in `each'
        from /usr/share/net-responsibility/lib/modules/db.rb:149:in `rotate_log'
        from /usr/local/bin/net-responsibility-report:97:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116

```
I'm not sure why you're getting that error. I'm working on a release that includes additional debugging info, so hopefully it will give some indication as to the problem. Stay tuned.
> I also checked to see if the report was going into the Junk folder of the hotmail account that I was trying to send it to and it wasn't in there, so I don't know what is going on with that.  It sends fine to all the other emails.
I wonder if Hotmail is rejecting the message because it's too long. Set your send from e-mail address to your regular e-mail and try again. See if you get any bounces back.
> **leetcharmer said:**
> How long should it take to go through?
24 hours at the absolute most. Two hours is a really long time. Normal time is within a minute.

Fire up mutt (or some other local mail reader) and see if postfix sent you any errors.

---

### Post by leetcharmer on 2007-11-09
> **mssever said:**
> 24 hours at the absolute most. Two hours is a really long time. Normal time is within a minute.

Fire up mutt (or some other local mail reader) and see if postfix sent you any errors.

It never went through, I don't know how to do mutt or any of the other local mail readers.

---

### Post by mssever on 2007-11-10
> **leetcharmer said:**
> It never went through, I don't know how to do mutt or any of the other local mail readers.

For mutt, ```
sudo aptitude install mutt
```Then type mutt to start it. It runs in a terminal.

---

### Post by paladinphil on 2007-11-14
Heya mssever, 

Thanks for coming up with a accountability app!  

I'm a total newbie to Ubuntu here, having made the switch a few weeks ago from windows.  I'm slowly learning my terminal code, and the backend of Ubuntu, after finding out that I need to have some basic linux knowledge to really make changes work on my laptop

I'm having a problem where I'm not getting the report to the email.  I've checked postfix, as far as I can understand, and I've also instead the mailx thing such that I recieve emails on my gmail account.  

Here's my error log:
```
net-responsibility-report[9145]: Generating report
net-responsibility-report[9145]: Sending report
net-responsibility-report[9145]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[9145]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[9145]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[9145]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[9145]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[9145]: => from /usr/local/bin/net-responsibility-report:116
/usr/lib/ruby/1.8/timeout.rb:54:in `rbuf_fill': execution expired (Timeout::Error)
        from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
        from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
        from /usr/lib/ruby/1.8/net/protocol.rb:132:in `rbuf_fill'
        from /usr/lib/ruby/1.8/net/protocol.rb:116:in `readuntil'
        from /usr/lib/ruby/1.8/net/protocol.rb:126:in `readline'
        from /usr/lib/ruby/1.8/net/smtp.rb:664:in `recv_response'
        from /usr/lib/ruby/1.8/net/smtp.rb:396:in `do_start'
        from /usr/lib/ruby/1.8/net/smtp.rb:686:in `critical'
        from /usr/lib/ruby/1.8/net/smtp.rb:396:in `do_start'
        from /usr/lib/ruby/1.8/net/smtp.rb:378:in `start'
        from /usr/lib/ruby/1.8/net/smtp.rb:316:in `start'
        from /usr/share/net-responsibility/lib/report_mailer.rb:76:in `send_message'
        from /usr/share/net-responsibility/lib/report_mailer.rb:97:in `create_and_send'
        from /usr/local/bin/net-responsibility-report:87:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116

```

Could you enlighten me with your skills of a Linux master?

---

### Post by scottie_z on 2007-11-20
Are you aware of the following project?

[http://www.accountabilitypal.org/]("http://www.accountabilitypal.org/")

It looks unmaintained, but there might be some useful code there.  I have no idea, but I just thought I'd point it out.

---

### Post by danoyoto on 2007-11-26
Is there an update on this?  Is it ready to use on a regular daily basis?

---

### Post by mssever on 2007-11-27
> **paladinphil said:**
> I'm having a problem where I'm not getting the report to the email.  I've checked postfix, as far as I can understand, and I've also instead the mailx thing such that I recieve emails on my gmail account.  

Here's my error log:
```
net-responsibility-report[9145]: Generating report
net-responsibility-report[9145]: Sending report
net-responsibility-report[9145]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[9145]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[9145]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[9145]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[9145]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[9145]: => from /usr/local/bin/net-responsibility-report:116
[B] /usr/lib/ruby/1.8/timeout.rb:54:in `rbuf_fill': execution expired (Timeout::Error)
        from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
        from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
        from /usr/lib/ruby/1.8/net/protocol.rb:132:in `rbuf_fill'
        from /usr/lib/ruby/1.8/net/protocol.rb:116:in `readuntil'
        from /usr/lib/ruby/1.8/net/protocol.rb:126:in `readline'
        from /usr/lib/ruby/1.8/net/smtp.rb:664:in `recv_response'
        from /usr/lib/ruby/1.8/net/smtp.rb:396:in `do_start'
        from /usr/lib/ruby/1.8/net/smtp.rb:686:in `critical'
        from /usr/lib/ruby/1.8/net/smtp.rb:396:in `do_start'
        from /usr/lib/ruby/1.8/net/smtp.rb:378:in `start'
        from /usr/lib/ruby/1.8/net/smtp.rb:316:in `start'
        from /usr/share/net-responsibility/lib/report_mailer.rb:76:in `send_message'
        from /usr/share/net-responsibility/lib/report_mailer.rb:97:in `create_and_send'
        from /usr/local/bin/net-responsibility-report:87:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116[/B]

```
I've put the relevant error message in bold. It appears  that Ruby (the program that actually powers Net Responsibility is timing out when it tries to send an e-mail. It is probably the fault of Postfix. If you try the following command, it will tell you if Postfix is working or not: ```
echo "Test message" | mail -s "Test subject" your@email.address
``` Unfortunately, I'm far from a Postfix expert.
> **scottie_z said:**
> Are you aware of the following project?

[http://www.accountabilitypal.org/](http://www.accountabilitypal.org/)

It looks unmaintained, but there might be some useful code there.  I have no idea, but I just thought I'd point it out.
I wasn't aware of it. Thanks for the link. I'll see if it has anything useful.
> **danoyoto said:**
> Is there an update on this?  Is it ready to use on a regular daily basis?
I'm using it on a regular daily basis. I haven't been developing it at the same pace I did initially, and there are still some bugs, but it works for the most part.

---

### Post by klawncare1212 on 2007-12-04
I am not running Ubuntu.  I had considered it, but settled on PCLinuxOS instead, which I've been pretty pleased with.  However, I ran across this thread while looking for an accountability software for Linux.  Haven't really found too much.

Does anyone know how easily this might install on a PCLinux machine?

---

### Post by mssever on 2007-12-05
> **klawncare1212 said:**
> I am not running Ubuntu.  I had considered it, but settled on PCLinuxOS instead, which I've been pretty pleased with.  However, I ran across this thread while looking for an accountability software for Linux.  Haven't really found too much.

Does anyone know how easily this might install on a PCLinux machine?

I've never used PCLinuxOS, but from their website it appears that they use .deb packages. Net Responsibility will probably work, unless PCLinux doesn't have some of the required dependencies available. But the only way to know would be to try it. I'm very interested in hearing whether it works on PCLinuxOS.

---

### Post by artesian_spring on 2007-12-07
Hey, thanks for making this!
net-responsibility is, as far as I recall, the first package I've successfully gotten from subversion and compiled--the README was straightforward and correct; the installation went off without a hitch once I got all the dependencies. 

Now how do I know if it is configured properly?

---

### Post by mssever on 2007-12-10
> **artesian_spring said:**
> Hey, thanks for making this!
net-responsibility is, as far as I recall, the first package I've successfully gotten from subversion and compiled--the README was straightforward and correct; the installation went off without a hitch once I got all the dependencies. 

Now how do I know if it is configured properly?

Thanks for the kind words! If everything's configured properly, it should be able to send out reports. If you want to send a report manually, type ```
sudo net-responsibility-report
``` If the message goes through, you're good to go. If not, first check Postfix's configuration. Try something like this: ```
echo "Test message" | mail -s "some subject" your@email.com
``` If that works, then something's wrong with your Postfix configuration. Otherwise, you've probably found a bug. In that case please post any error messages you get.

---

### Post by twin_57103 on 2007-12-20
> **mssever said:**
> Yes, postfix is misconfigured. Run ```
sudo dpkg-reconfigure postfix
``` You should be able to pretty much accept the defaults. Here's a screen-by-screen run through (I'm running Feisty; it might be different in other versions):[LIST]
[*]Choose Internet site on the first screen
[*]Choose (or accept) your machine's mail name. e.g., I use scott-laptop.mss
[*]Enter your system username
[*]Don't worry too much about the next screen since you won't be receiving mail directly
[*]Choose No
[*]Enter 127.0.0.0/8
[*]For the rest of the options, you can just accept the default.[/LIST]After reconfiguring, try running the test I gave you again.

I am trying to set up this software for a friend.  I've been trying to get postfix configured properly, but I'm having some trouble.

I've chosen internet site, then "alf", which is the user's login name (I've also tried "alf-desktop", which does not work, either), then /var/mail/alf, then "alf-desktop, localhost.localdomain, , localhost_", then no, then 127.0.0.0/8, and accepted the defaults on the last several pages.

The test message code does not send anything:
alf@alf-desktop:~$ echo "Test message" | mail -s "Test subject" [email address suppressed]

Here is the output from the net responsibility report.
alf@alf-desktop:~$ sudo net-responsibility-report
net-responsibility-report[9871]: Generating report
net-responsibility-report[9871]: Sending report
net-responsibility-report[9871]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[9871]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[9871]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[9871]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[9871]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[9871]: => from /usr/local/bin/net-responsibility-report:116
/usr/share/net-responsibility/lib/modules/db.rb:160:in `rotate_log': undefined method `close' for nil:NilClass (NoMethodError)
        from /usr/share/net-responsibility/lib/modules/db.rb:149:in `each'
        from /usr/share/net-responsibility/lib/modules/db.rb:149:in `rotate_log'
        from /usr/local/bin/net-responsibility-report:97:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116

Is there any help you can give to get this configured properly?
Thanks!

---

### Post by mssever on 2007-12-20
> **twin_57103 said:**
> The test message code does not send anything:
alf@alf-desktop:~$ echo "Test message" | mail -s "Test subject" [email address suppressed]
In your e-mail, I believe you told me that mail is now going through. Correct me if I'm wrong.
> Here is the output from the net responsibility report.
alf@alf-desktop:~$ sudo net-responsibility-report
net-responsibility-report[9871]: Generating report
net-responsibility-report[9871]: Sending report
net-responsibility-report[9871]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[9871]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[9871]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[9871]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[9871]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[9871]: => from /usr/local/bin/net-responsibility-report:116
**[COLOR=Red] /usr/share/net-responsibility/lib/modules/db.rb:160:in `rotate_log': undefined method `close' for nil:NilClass (NoMethodError)[/COLOR]**
        from /usr/share/net-responsibility/lib/modules/db.rb:149:in `each'
        from /usr/share/net-responsibility/lib/modules/db.rb:149:in `rotate_log'
        from /usr/local/bin/net-responsibility-report:97:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116This is a different error than the previous error. There's a workaround for this problem in the works, but for now, try again and see if you still keep getting that same error. I've highlighted the key line in the message above.

---

### Post by BLTicklemonster on 2007-12-20
??? spyware for linux?

---

### Post by mssever on 2007-12-21
> **BLTicklemonster said:**
> ??? spyware for linux?
Sorta, but not really. A person installs accountability software fully aware that it will log their Internet access and e-mail out that log. But it only goes to user-provided e-mail addresses. So in essence, this software is for people who WANT someone to spy on them. It's all out in the open; no hidden agenda.

---

### Post by bjaurelio on 2007-12-23
it's working now. not sure what i did, but perhaps i just needed to wait a little while to get the emails.

---

### Post by semijoyful on 2008-01-05
Is there a way that I can run this program on 64bit Gutsy?  I am somewhat of a nOOb at this, but I would appreciate anything on this.
Thanks!

Ninjakirk

---

### Post by mssever on 2008-01-09
> **semijoyful said:**
> Is there a way that I can run this program on 64bit Gutsy?  I am somewhat of a nOOb at this, but I would appreciate anything on this.
Thanks!

Ninjakirk
Have you tried installing Net Responsibility? It seems to me like it should run under 64-bit. However, since I don't have any 64-bit machines, I can't really test it. Does anyone else have experience running under 64-bit?

(Sorry for the delayed response. I was out of town.)

---

### Post by semijoyful on 2008-01-09
Thanks for the reply!  Actually, I tried downloading the .deb package, but my package manager says that it's the incorrect architecture and will not install.
Cheers!

Ninjakirk

---

### Post by mssever on 2008-01-11
> **semijoyful said:**
> Thanks for the reply!  Actually, I tried downloading the .deb package, but my package manager says that it's the incorrect architecture and will not install.
Cheers!

Ninjakirk

The package must have been built architecture-specific--even though Net Responsibility doesn't care. If you download the source and follow the instructions, you should be able to build it without too much trouble.

---

### Post by jgt157 on 2008-01-12
I'm trying to install this on kubuntu and the installation doesn't appear to have worked.  I don't see any of the net-responsibillity files on my system.  I used the .deb installation.  Any ideas?

JimT

---

### Post by mssever on 2008-01-13
> **jgt157 said:**
> I'm trying to install this on kubuntu and the installation doesn't appear to have worked.  I don't see any of the net-responsibillity files on my system.  I used the .deb installation.  Any ideas?

JimT

You mean that /usr/share/net-responsibility doesn't exist? That's where the majority of the files live. If those files don't exist, then try re-installing. I can't imagine how the deb package could say it installed without actually installing anything.

Note that there really isn't a graphical user interface. The configuration menu item merely opens up a terminal. Since I'm not a KDE user, I don't know whether KDE picks up the menu item or not. It should, according to the freedesktop.org spec. Try typing ```
sudo net-responsibility-config
``` That should start the configuration program.

---

### Post by lyve on 2008-01-16
Thanks mssever for creating this.  It's something I definitely need.  Now I'm hoping for some help to get it up and running.

I recently installed Gutsy, so it is still pretty clean.  I installed the Net Responsibility.deb without a problem.  I think I made a mistake with my initial configuration of Postfix, so I reconfigured it.  Now I'm trying to test postfix using "echo "Test message" | mail -s "Test subject" <e-mail address suppressed>" but I'm getting an error that "mail" command doesn't exist.  I feel pretty silly because this is a basic thing, but I appreciate any help.  Thanks.

---

### Post by dardack on 2008-02-11
Is this still an active project?  I actually dropped linux and went with windows just for Covenant Eyes.  If there was something I could get for linux like this, i would be stoked.  

If it is still active, is there a way to have my wife set some master password so I could never turn it off?

Not related to this project, but are people using this in conjunction with something else like dansguardian or something?

---

### Post by mssever on 2008-02-12
> **dardack said:**
> Is this still an active project?  I actually dropped linux and went with windows just for Covenant Eyes.  If there was something I could get for linux like this, i would be stoked.  

If it is still active, is there a way to have my wife set some master password so I could never turn it off?

Not related to this project, but are people using this in conjunction with something else like dansguardian or something?
I haven't had a lot of time to put into this project lately. It isn't dead, but it's in hibernation. :)

A standard master password won't work on Linux, because root can bypass anything. Net Responsibility does log when it's turned off. You could alter the sudoers file such that your wife is the only one who can start or kill Net Responsibility or make further changes to sudoers. I'm afraid I don't know enough about sudoers to be able to tell you what to do, though.

---

### Post by mssever on 2008-02-12
> **lyve said:**
> Now I'm trying to test postfix using "echo "Test message" | mail -s "Test subject" <e-mail address suppressed>" but I'm getting an error that "mail" command doesn't exist.  I feel pretty silly because this is a basic thing, but I appreciate any help.  Thanks.

Sorry for the long delay in responding. I wasn't intentionally ignoring you. Somehow, I just never saw your question until now. :oops:

The mail command is part of the mailx package. Make sure that's installed. If It is, then I don't know what the problem is.

---

### Post by waspinator on 2008-02-13
I'm not sure how this would fit into this project (if at all), but are there any plans on/to:

1. Creating separate logs for separate users
2. Show the most visited websites (top 10)
3. Show websites that were blocked by dansguardian
4. Show Logon Times
5. Show Applications Run
6. Show Media Run
7. Show Emails Sent/Received (with content)
8. Show Instant Messaging Conversations

If this project does not concern itself with such information is there something else for Ubuntu that does?

---

### Post by mssever on 2008-02-14
> **waspinator said:**
> 1. Creating separate logs for separate usersThe way this is written, it isn't possible to determine which process--and therefore which user--is responsible for any particular traffic. I'd be open for suggestions on how to get that information.
> 2. Show the most visited websites (top 10)That shouldn't be too difficult to add.
> 3. Show websites that were blocked by dansguardianShouldn't that be dansguardian's responsibility?
> 4. Show Logon TimesIt does log when it was started (generally on boot). It doesn't log logins. I suppose it could be made to do that, but that's not likely to become a priority feature. I think that logging user processes would be best handled by a separate program.
> 5. Show Applications Run
6. Show Media RunAdding these features would significantly broaden the scope of this program. While it might be a useful feature, it would be a major undertaking.
> 7. Show Emails Sent/Received (with content)
8. Show Instant Messaging ConversationsRight now, I don't know how to get at network traffic other than HTTP traffic. I could sniff raw traffic, but that would be a whole lot of work to analyze correctly and debug. I currently depend on urlsnarf to do that job, and urlsnarf is limited in what it can do. Also, monitoring email is difficult because many people use web-based email, which means that the program would have to read every page, decrypt it, and analyze it. That's more in dansguardian's domain.

---

### Post by Niklas Schröder on 2008-02-17
It may have already been mentioned (I don't have time to read the entire thread), but it would be a nice addition to be able to change the frequency of the send times.  Swapping from once a week to once a day would be good.  I'm a major net browser and it would be VERY time consuming for my peers to review my log after I've browsed for a whole week.  ;)

It might also be a good idea to find a way to disable disabling the process.  :p

---

### Post by theophile on 2008-02-18
I am very interested in this project and would like to get it working.

My problem now is that, though I have postfix working, it will not send emails because I am on DSL and my IP is blacklisted. I cannot reliably get postfix's relaying to work. I notice from the config that you've at least started to implement directly sending through an SMTP server with authentication. I think this is the best route and I don't think I can use this until that is possible.

Also, with regard to "root-proofing" it as some have mentioned, I don't think that will be possible. By definition, root can do anything. The only alternative I can think of is a solution which essentially gives my user account permission to "sudo" absolutely anything - except the net-responsibility processes, logs, and configs - and let my wife set the root password.

---

### Post by teachtheword on 2008-02-18
My son is using the Net Responsibility Report on his small laptop.  He has covenant eyes on his desk top.  Is the report suppose to say shutdown and startup everytime the computer turns off or just when the program has been disabled?  I think fear he is disabling it.  I thought the shutdown and startup was only for when it was starting up the first time.  All the other times should just be start times correct?

Thanks,
Cheryl

---

### Post by mssever on 2008-02-19
> **Niklas Schröder said:**
> It may have already been mentioned (I don't have time to read the entire thread), but it would be a nice addition to be able to change the frequency of the send times.  Swapping from once a week to once a day would be good.  I'm a major net browser and it would be VERY time consuming for my peers to review my log after I've browsed for a whole week.  ;)
Yes, that would be a good configuration option. However, it would take a bit of work to implement it. Right now, the installer simply drops a symlink in /etc/cron.weekly. To be able to fine-tune the frequency, it would probably require a script in /etc/cron.hourly that would read the configured frequency and only run the report that often. It's certainly doable, though.
> **theophile said:**
> My problem now is that, though I have postfix working, it will not send emails because I am on DSL and my IP is blacklisted. I cannot reliably get postfix's relaying to work. I notice from the config that you've at least started to implement directly sending through an SMTP server with authentication. I think this is the best route and I don't think I can use this until that is possible.Actually, I put that into the config when I first started to think about e-mail. I agree that Postfix is a poor solution. The majority of bug reports I've gotten have been related to people not configuring Postfix correctly. And since I'm no Postfix expert, I can't help them very well.

Last I looked, I couldn't find a Ruby SMTP library to use, and I don't know enough about SMTP to write my own. That's why I'm using Postfix. But if I can find a suitable library to use, I'd love to switch.

> Also, with regard to "root-proofing" it as some have mentioned, I don't think that will be possible. By definition, root can do anything. The only alternative I can think of is a solution which essentially gives my user account permission to "sudo" absolutely anything - except the net-responsibility processes, logs, and configs - and let my wife set the root password.You're right. It *is* possible to use visudo to alter what sudo allows, as you mentioned. What you'd need to restrict:[LIST=1]
[*]The commands kill, killall, visudo (and directly editing sudoers, though you shouldn't do that, anyway), and net-responsibility-*
[*]Editing of /var/log/net-responsibility.log. If that isn't possible, then you'd have to restrict the command sqlite3[/LIST]> **teachtheword said:**
> My son is using the Net Responsibility Report on his small laptop.  He has covenant eyes on his desk top.  Is the report suppose to say shutdown and startup everytime the computer turns off or just when the program has been disabled?  I think fear he is disabling it.  I thought the shutdown and startup was only for when it was starting up the first time.  All the other times should just be start times correct?

It logs whenever net-responsibility-daemon is started and stopped. I haven't figured out how to determine whether it is stopping because the computer was shut down or because someone killed it so they could mess up with impugnity.

---

### Post by theophile on 2008-02-19
A couple of ideas for differentiating manual shutdowns from computer rebooting/suspending:

It looks like the logfile is binary, which is good (prevents tampering). Perhaps there is a way for the logfile to reflect time periods in which the machine is running but the net-responsibility process is not. Maybe inotify would come in handy here? The closer net-responsibility can get to running at kernel-level the better! :-D

One other thought, can sudo be configured in such a way to not allow certain processes run by root to be killed? This would seem a better solution than restriction permissions to "kill" and "killall" entirely because I use those rather frequently on processes run amok.

As far as SMTP in Ruby, I am not a programmer (unfortunately), but would this be of help?
[http://ruby.about.com/od/tutorials/ss/ruby_email.htm](http://ruby.about.com/od/tutorials/ss/ruby_email.htm)

---

### Post by wolfear on 2008-02-19
> **mssever said:**
> I've been working on an Internet accountability program for Linux. The idea is to log the websites you visit, then periodically e-mail that log so someone else. It also writes a log entry when it is shutdown.

Ok..i gotta ask..who are you working for?
This sounds like just the sort of thing RIAA and certain other orgs/corps would dream up.

---

### Post by theophile on 2008-02-19
> **wolfear said:**
> Ok..i gotta ask..who are you working for?
This sounds like just the sort of thing RIAA and certain other orgs/corps would dream up.
It's an attempt to implement the functionality in [this program](http://www.covenanteyes.com/help_and_support/article/basic_description_of_the_covenant_eyes_accountability_program/?c=20).

---

### Post by mssever on 2008-02-20
> **theophile said:**
> It looks like the logfile is binary, which is good (prevents tampering). Perhaps there is a way for the logfile to reflect time periods in which the machine is running but the net-responsibility process is not. Maybe inotify would come in handy here? The closer net-responsibility can get to running at kernel-level the better! :-DThe only way the logfile can reflect those periods is for Net Responsibility to be running so that it can update the logfile. But as long as Net Responsibility is running, there's no need for such functionality... :)

I'm not a C programmer (yet) so I'm not familiar with inotify. According to the man page, it's for monitoring changes to files, which isn't relevant to the problem at hand.

Implementing all or part of Net Responsibility as a kernel module would be a gigantic undertaking. First, I'd have to learn C and the particulars of kernel hacking. Then I'd have to rewrite all or a major portion on Net Responsibility in C (which would require a lot more code, be buggier, and drastically increase development time). Then, if I wanted to provide .debs, I'd have to compile the module for every kernel and recompile every time a new kernel is released. While a kernel module would solve some problems, it would create many more. (Of course, if someone else is interested in writing such a module, be my guest.)

EDIT: By the way, the logfile is a binary file, but it's in a well-known format that isn't tamper-proof. Designing a custom binary format whould probably just end up bug-ridden and slow. Better to use a combination of Linux permissions and sudo configuration to protect the file.
> One other thought, can sudo be configured in such a way to not allow certain processes run by root to be killed? This would seem a better solution than restriction permissions to "kill" and "killall" entirely because I use those rather frequently on processes run amok.It's been quite a while since I've read the sudoers man page, so I don't remember what all is possible. However, I do know that what you're asking isn't completely possible through sudoers alone. SIGKILL cannot be trapped. It goes straight to the kernel and the kernel itself immediately kills the process (not necessarily in a nice way; it's roughly equivalent to pulling the power cable instead of using the shut down command). Since kill is capable of sending SIGKILL (kill -9), the only way to keep someone from killing Net Responsibility would be to either prohibit the use of kill or modify kill to check some list of programs it can't send signals to.

> As far as SMTP in Ruby, I am not a programmer (unfortunately), but would this be of help?
[http://ruby.about.com/od/tutorials/ss/ruby_email.htm](http://ruby.about.com/od/tutorials/ss/ruby_email.htm)I'm surprised that About.com actually has some mildly useful information! Unfortunately, it doesn't address secure SMTP connections, which is where I have a problem. I run all my e-mail through Gmail, and Gmail requires a secure connection. So even if I supported non-secure SMTP connections, I couldn't test it (or debug it) because my service requires secure connections. And I'm guessing that every other *intelligent* service does the same.
> **wolfear said:**
> Ok..i gotta ask..who are you working for?
This sounds like just the sort of thing RIAA and certain other orgs/corps would dream up.
Hmm.... If I were working for the RIAA to come up with an evil scheme to spy on the innocent public, discussing the scheme on a place like ubuntuforums would cause the scheme to be exposed. :)

There's nothing evil in this program. Read the source code if you're not convinced. It does exactly what it says it does and people install it voluntarily with full knowledge of what it does. If you don't like some program monitoring the websites you visit, don't install it.

This is purely a volunteer project. I'm not making any money from it (though donations are welcome :)).
> **theophile said:**
> It's an attempt to implement the functionality in [this program]("http://www.covenanteyes.com/help_and_support/article/basic_description_of_the_covenant_eyes_accountability_program/?c=20").
More accurately, it's the same basic kind of program. I've never used any accountability program other than Net Responsibility (because to my knowledge my program is the only one available for Linux) and I'm not attempting to clone some other program.

---

### Post by Auslegung on 2008-02-27
I didn't read every single post so I apologize for double-posting, but is this thing cross-platform yet?  My buddy and I want to have an accountability program, but he uses Windoze and I use, of course, Ubuntu.  If this is not cross-platform, is there another program that is, that anyone is aware of?

---

### Post by mssever on 2008-02-27
> **Auslegung said:**
> I didn't read every single post so I apologize for double-posting, but is this thing cross-platform yet?  My buddy and I want to have an accountability program, but he uses Windoze and I use, of course, Ubuntu.  If this is not cross-platform, is there another program that is, that anyone is aware of?

No, Net Responsibility isn't cross-platform. Delving into the network stack to intercept Internet traffic isn't very portable. Plus, I'm not a Windows programmer, and learning to program in a Windows environment would require me to actually use Windows. I'm not interested in that kind of pain. :) That said, if someone can figure out how to make this program cross platform (such as by finding a Windows version of urlsnarf), and is willing to do the work, I'd be willing to include it.

As to whether there's another program that is cross platform, as far as I know, Net Responsibility is the only accountability program that runs on Linux.

All that aside, there's no reason why the two of you couldn't use different programs. Net Responsibility sends its reports via e-mail, and the Windows programs can either send e-mail or work through a website. Plus, the Windows programs have additional useful features, so a Windows user would probably be better off running one of those.

---

### Post by danradigan on 2008-03-20
Hey Scott-

Is there a way to trim down the report that gets sent to just the domains?  I'm thinking it might be clearer to just have the domains listed out sorted back to front with number of hits.

For example:

320 gamma.myspace.com
500 zed.somesite.com
10   img.yahoo.com
30  mail.yahoo.com

Why do you include all the get/post requests as well?

dan

---

### Post by Niklas Schröder on 2008-03-20
what would be the proper way to set this up to work with gmail?  i haven't gotten a report in three weeks...

---

### Post by mssever on 2008-03-20
> **danradigan said:**
> Is there a way to trim down the report that gets sent to just the domains?  I'm thinking it might be clearer to just have the domains listed out sorted back to front with number of hits.

For example:

320 gamma.myspace.com
500 zed.somesite.com
10   img.yahoo.com
30  mail.yahoo.com

Why do you include all the get/post requests as well?
Well, I never thought about that. At one time, I allowed filtering out common, harmless sites (such as ubuntuforums). But other users rightly pointed out that such a feature could easily be abused. So, I reverted back to full output.

If a website analysis tool were ever written, full output would be important because it would be possible to filter the data, and there are presumably ways to get at bad websites through innocuous domain names.

However, since such a website isn't available (or even currently in the works), your suggestion has a lot of merit. If you surf the web a lot, then the full report is too tiresome for anyone to read. (In thinking aloud, I wonder if it should send TWO emails: one with abbreviated data, and one with full data; that way your accountability partner could have access too all data if he/she felt it necessary.)
> **Niklas Schröder said:**
> what would be the proper way to set this up to work with gmail?  i haven't gotten a report in three weeks...

The released version doesn't support sending email through Gmail or similar, because I've never been able to get encrypted sessions to work (Gmail requires such). However, Chad Aeschlimansent me a patch via e-mail that's intended to provide such a feature. I created a separate Subversion branch for it. You can checkout a copy of that code with the following command: ```
svn checkout https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/smtp_encryption net-responsibility
```Read the file README for build instructions. You will get a .deb which you can then install.

Note, though, that this branch is unstable. Chad said his code worked for him, but I never got it working for me (in fairness, I made some changes which might have broken his patch). In other words, it might or might not work.

EDIT: You might also be experiencing a known bug. If your logfile (/var/log/net-responsibility.log) grows too large (due to an inability to send mail often enough), then there comes a point where Net Responsibility can no longer handle it. The only thing you can do is delete the logfile (after stopping Net Responsibility). I'm pretty sure that the bug isn't in my code (I think it's in Ruby's SQLite library), but I don't know how to work around it.

---

### Post by bsalt on 2008-04-04
Thank you mssever for taking the initiative to write this application. I've been away from the forums for a while, but I've been watching this application evolve.

---

### Post by tgreene50 on 2008-04-06
First of all, let me say that I am new to Ubuntu and I like what I see.  I was looking for a porn accountability software similar to what x3 is, and I have come across this thread.

I also want to applaud all the developer that is working on the CE of Ubuntu because as a recovered porn addict, I cannot stress the importance of accountability, especially with the wide open philsophy of the New Age that anything goes, so I applaud your effort to take a stand against the enemy of the darkness.

Keep fighting the good faith like a good soldier of Jesus Christ!

I downloaded Net Responsibility and got the following error: Dependency is not satisfiable: ruby.

Is there anything I need to download or add?

---

### Post by mssever on 2008-04-06
> **tgreene50 said:**
> I downloaded Net Responsibility and got the following error: Dependency is not satisfiable: ruby.
That's odd... Try manually installing ruby from Synaptic. (You might need to enable the universe repository; I don't remember which repo ruby is in.)

---

### Post by tgreene50 on 2008-04-06
> **mssever said:**
> That's odd... Try manually installing ruby from Synaptic. (You might need to enable the universe repository; I don't remember which repo ruby is in.)

I am not sure exactly what to look for.  I did a search within the Synaptic and came across this: libgtksourceview2.0-common (which is installed on my machine, I am assuming), and vim-common.  The search string I used was "ruby."  I'm not quite sure if that what you were suggesting.

---

### Post by mssever on 2008-04-07
> **tgreene50 said:**
> I am not sure exactly what to look for.  I did a search within the Synaptic and came across this: libgtksourceview2.0-common (which is installed on my machine, I am assuming), and vim-common.  The search string I used was "ruby."  I'm not quite sure if that what you were suggesting.

The package is called ruby. Make sure that the main and universe repositories are enabled. After you've done that, run ```
sudo aptitude update && sudo aptitude install ruby
``` If that still doesn't work, please post the contents of your /etc/apt/sources.list.

---

### Post by tgreene50 on 2008-04-08
I tried to install Ruby using all the libraries it comes with using Synaptic.  No such luck, and it appears that Ruby 1.8.dev is obsolete.  The new version, from what I gather in other General Help forums, and reading through the installation is 1.9.  To be perfectly honest, using the Synaptic and the Terminal is somewhat confusing.  I thought that Linux was supposed to be far more simpler than using Windows.

Good news!  I finally got the program to install and run perfectly!  Baw-ha-ha-ha!  I found this link very useful: [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)  Apparently, I did not have the Universe and Main repos set up in the Software Source and in the Add/Remove App preference.  It's all good nows.  Thanks man for your patience and help.  I'm glad to have this program on the machine, and it gives my wife and myself a peace of mind knowing that I am being held accountable for my surfing of the Internet.  God bless for making this program!

---

### Post by Theophilosity on 2008-04-09
Hi!
Looks like a great project, and I hope to jump onboard for testing soon. My Linux use is limited to LiveCD's at work (depot technician) and virtual machines at home. The problem any Linux accountability software is bound to be that we are mostly admins and hackers, and Linux is just too doggone admin-friendly. It sounds like you already have a hefty list of future features, and I don't want to overburden you, but...

Logging on a web server is to be preferred, if possible. This prevents modification of the log file, gives you report filtering options, and might even open options to distinguish a shut down from an abnormal termination. I know this adds layers of difficulty to development, and probably won't be happening anytime soon, but I would certainly encourage that this would be a good eventual goal.

Also, has anyone made the Covenant Eyes people aware of this project? I've been bugging them in emails to start working on a solution for Linux (and Win Mobile) so I can go native, and they might be able to learn a lot from what you're already doing. They have the advantage of programming accountability software as their full-time job, so a little collaboration might go a long way toward producing a solution, assuming everyone was agreeable to it.

I don't mean to sound arrogant by what I'm saying - I'm definitely a n00b compared to a lot of you guys, but I didn't want that to stop me if I might accidentally end up saying something important. Thanks for listening!

---

### Post by dasunst3r on 2008-04-09
Have you considered integrating this with something like DansGuardian?  Logging *everything* could cause an "information overflow," if you will.  If you log only the attempts to visit inappropriate sites, then this will be better.

---

### Post by mssever on 2008-04-09
> **tgreene50 said:**
> it appears that Ruby 1.8.dev is obsolete.  The new version, from what I gather in other General Help forums, and reading through the installation is 1.9.  . . . I found this link very useful: [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)  Apparently, I did not have the Universe and Main repos set up in the Software Source and in the Add/Remove App preference. 
Glad you got it working. Here are a few notes:

[LIST]
[*]You don't need ruby1.8-dev.
[*]Ruby 1.9 is the development version of ruby, not the stable version. I haven't tested Net Responsibility in 1.9.
[*]Net Responsibility has nothing to do with Rails.
[*]Yes, repos would be the first thing to check, which is why I suggested that earlier.[/LIST] > **Theophilosity said:**
> The problem any Linux accountability software is bound to be that we are mostly admins and hackers, and Linux is just too doggone admin-friendly.Therein lies the difficulty. This is also why blocking programs are ineffective. They're too easy to circumvent. Technically, it isn't necessary to prevent modicifation of the file; it's only important to be able to reliably detect tampering. But that's easier said than done. Your web server logging suggestion is quite interesting for that reason. It's definitely going on the wishlist.

> **dasunst3r said:**
> Have you considered integrating this with something like DansGuardian?  Logging *everything* could cause an "information overflow," if you will.  If you log only the attempts to visit inappropriate sites, then this will be better.
I don't know too much about working with dansguardian, because it wouldn't even start up when I installed it.

I think that logging everything is important to prevent tampering. I think that the proper solution is to have a good log analysis tool (which currently doesn't exist).

---

### Post by tgreene50 on 2008-04-13
Hey everybody!  It's been a while since I checked this thread.  mssever: why then did the OS say that it needed to have Ruby installed before the program could run?  That's strange if you said it had nothing to do with Ruby or Rails.

Also, I found a website that gave Google's Gmail address protocol, since I saw some people complaining that their accountability partner could not receive their report through Gmail.  I found this information at the following website: [http://www.emailaddressmanager.com/tips/mail-settings.html](http://www.emailaddressmanager.com/tips/mail-settings.html)

Scroll down and you will see the setting for Gmail over their secure connection.  Hope this help y'all in a greater detail.

Cheers!

---

### Post by mssever on 2008-04-13
> **tgreene50 said:**
> why then did the OS say that it needed to have Ruby installed before the program could run?  That's strange if you said it had nothing to do with Ruby or Rails.I didn't say that it has nothing with Ruby or Rails. I said that it has nothing to do with Ruby on Rails. You do need Ruby. That's the language Net Responsibility is written in. But Ruby != Rails. Ruby is a programming language. Ruby on Rails is a (poorly-named) web application framework built on top of Ruby. A better name would be Rails on Ruby, but I suppose that doesn't have quite the ring to it. Net Responsibility doesn't use Rails.

> Also, I found a website that gave Google's Gmail address protocol, since I saw some people complaining that their accountability partner could not receive their report through Gmail.  I found this information at the following website: [http://www.emailaddressmanager.com/tips/mail-settings.html](http://www.emailaddressmanager.com/tips/mail-settings.html)Thanks for digging this up. This is the same info that's available directly from the Gmail website. The problem is that Net Responsibility (the main branch, at least) doesn't know how to make a secure connection to Gmail.

---

### Post by dasunst3r on 2008-04-13
If **everything** must be logged, then the analysis tool should present a collapsible "tree" view, like this:
```

xyz.com
  |-/abc/
      |-anImage.gif
xyz.net
  |-/def/
      |-anotherImage.gif

```

Again, my intention is to prevent the monitoring person from becoming overwhelmed with information (since he/she *is* human).

---

### Post by mssever on 2008-04-14
> **dasunst3r said:**
> If **everything** must be logged, then the analysis tool should present a collapsible "tree" view
Yes, this was my idea, though I also want additional sorting and filtering capabilities.

---

### Post by Theophilosity on 2008-04-15
> **mssever said:**
> Yes, this was my idea, though I also want additional sorting and filtering capabilities.
Such as, filtering out adclick-type sites, or just viewing a log of jpeg's over a certain size? Also, are you logging times and such? CEyes (which I know you're not trying to emulate) markets to businesses, internet addicts, porn addicts and parents alike. Part of its appeal beyond the basic issue of lust is that it keeps track of what hours the internet is accessed. Just a thought. BTW, is there any sort of official wishlist or bug tracker, etc. out there for Net R yet?

---

### Post by javajoe220 on 2008-04-15
I just came across this - This is fantastic!  thank you for working on this.

I installed the deb with no issues and then configured and started the service.  But when I run 

sudo net-responsibility-report 

I get the following error:

net-responsibility-report[32717]: Generating report
net-responsibility-report[32717]: Sending report
net-responsibility-report[32717]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[32717]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[32717]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[32717]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[32717]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[32717]: => from /usr/local/bin/net-responsibility-report:116
/usr/lib/ruby/1.8/net/protocol.rb:206:in `initialize': Connection refused - connect(2) (Errno::ECONNREFUSED)
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `new'
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `old_open'
        from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
        from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
        from /usr/lib/ruby/1.8/net/protocol.rb:206:in `old_open'
        from /usr/lib/ruby/1.8/net/smtp.rb:393:in `do_start'
        from /usr/lib/ruby/1.8/net/smtp.rb:378:in `start'
        from /usr/lib/ruby/1.8/net/smtp.rb:316:in `start'
        from /usr/share/net-responsibility/lib/report_mailer.rb:76:in `send_message'
        from /usr/share/net-responsibility/lib/report_mailer.rb:97:in `create_and_send'
        from /usr/local/bin/net-responsibility-report:87:in `initialize'
        from /usr/local/bin/net-responsibility-report:116:in `new'
        from /usr/local/bin/net-responsibility-report:116

can you help with this?  Thanks!

---

### Post by javajoe220 on 2008-04-15
UPDATE:

I found the same issue on other postings and here is where I'm at:

"mail" is available in both the mailx and mailutils packages.  First I tried mailx and ran the command:

echo "Test message" | mail -s "Test subject" <my email address>

 I get the following error:
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed

I then removed mailx and installed mailutils and ran the same command.
I get no error but I get no email either.

sudo net-responsibility-report  still produces the same error.

Anyone have any thoughts?
I have outgoing mail set to "localhost" port 25
Do I need to install a mail server?

Thanks!

---

### Post by javajoe220 on 2008-04-15
RESOLVED

Two issues:
1) I was missing sendmail.  After I installed mailx and sendmail the command

echo "Test message" | mail -s "Test subject" <my email address>

now works;

2) However, sendmail uninstalled  Net Responsibility.  

So I grabbed the source from svn (I had downloaded the deb previously from sourceforge), built and installed the deb and now things seem to be working spiffy.

---

### Post by mssever on 2008-04-15
> **Theophilosity said:**
> Such as, filtering out adclick-type sites, or just viewing a log of jpeg's over a certain size? Also, are you logging times and such? CEyes (which I know you're not trying to emulate) markets to businesses, internet addicts, porn addicts and parents alike. Part of its appeal beyond the basic issue of lust is that it keeps track of what hours the internet is accessed. Just a thought. BTW, is there any sort of official wishlist or bug tracker, etc. out there for Net R yet?
Good suggestions, all of them. I haven't thought through exactly how the filtering could work; I'm not really to that stage yet.

There is both a bug tracker and a wishlist on the [Sourceforge page]("https://sourceforge.net/tracker/?group_id=205710"). So far, I haven't posted anything there, and neither has anyone else, but it would be good to start using it. Feel free to add feature requests.

In fact, if somebody has some time available and would like to help, they could read through this thread and add the bugs and feature requests that are in the thread and haven't already been fixed. That'll take some time, but it would be quite helpful. Earlier in the project, I worked on it pretty much every day, so it was no problem to keep everything in my head. But now, I don't remember everything, and a forum thread isn't the best way to document that stuff.
> **javajoe220 said:**
> RESOLVED
Glad you got it resolved. I'm actually working right now on implementing proper SMTP to avoid your issue in the future. The most commonly-reported problems have to do with Postfix problems. If everything goes well, the Postfix dependency and all its related problems will soon be history.

One caution (don't know if I've documented it elsewhere, so I'll say it here): Since you installed the SVN version, if you ever want to switch to the released version you'll have to uninstall the SVN version first; the way the SVN version numbers work, they always appear higher to APT than any release. That's probably a bug in Net Responsibility.

---

### Post by mssever on 2008-04-17
Good news! I've added proper SMTP support to Net Responsibility so that it can send e-mail through Gmail or your ISP. That means no more dependency on Postfix, which has been the biggest source of reported problems.

Since this is a fairly major change and only tested by me, it's in a separate Subversion branch. Please test this and confirm that it works. Once I get a few confirmations, I'll merge it into trunk, then do a release.

Since this is only available in svn (Subversion) right now, here are the commands for getting and building the latest version:

```
sudo aptitude install subversion epm
mkdir -p net-responsibility/branches
cd net-responsibility/branches
svn checkout https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/smtp-python smtp-python
cd smtp-python
./configure-packages
sudo ./make_deb.sh
gdebi-gtk linux*/netresponsibility-svn.*.deb
``` Once Net Responsibility is installed, run ```
./clean
```You'll need to re-run the configuration program before you can use the new Net Responsibility.

---

### Post by Pursuer on 2008-04-21
I downloaded this program, but when I went to install it, It said: **Only one software management tool is allowed to run at the same time**  Please close the other application e.g. 'Update Manager'. 'aptitude' or 'Synaptic' first.

I already shut down my Update Manager, but have no idea what it is talking about  for "aptitude" or "Synaptic."

Any help would be appreciated! :)

---

### Post by Kaaiman on 2008-04-21
You should try to log in again. Press Ctrl+Alt+Backspace to go quickly to the login screen. Warning: make backups of your open documents, or just logoff the usual way. :)

---

### Post by Pursuer on 2008-04-21
I shut down my computer and started again, but just got the same message.
I did notice that it says I need an "extra" download of something called postfix...?

---

### Post by mssever on 2008-04-21
> **Pursuer said:**
> I shut down my computer and started again, but just got the same message.
I did notice that it says I need an "extra" download of something called postfix...?
Yes, you need to install Postfix if you want to use the version you have. But see [post 134]("http://ubuntuforums.org/showpost.php?p=4736486&postcount=134"), which doesn't require postfix. It's about an experimental version that should be quite an improvement over the last release. I'm looking for some people to tell me whether it works for them before I make an official release. So far, nobody has responded. I wish someone would so I can go ahead and release it.

---

### Post by javajoe220 on 2008-04-22
I've tried out the new version and here are the results:

In a nutshell, GMail requires either port 465 or 587, 587 works but 465 produced an error.

I confirmed gmail sent the message by checking the "sent mail" folder.

First I ran:

```

sudo apt-get purge net-responsibility

```

Then I followed the steps above and configured the install

It started fine.

Port 465 produced the following error when I ran the report:

```

net-responsibility-report[31576]: Generating report
net-responsibility-report[31576]: Sending report
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 64, in <module>
    s = SMTP(smtpinfo['server'], smtpinfo['port'])
  File "/usr/lib/python2.5/smtplib.py", line 244, in __init__
    (code, msg) = self.connect(host, port)
  File "/usr/lib/python2.5/smtplib.py", line 311, in connect
    (code, msg) = self.getreply()
  File "/usr/lib/python2.5/smtplib.py", line 352, in getreply
    line = self.file.readline()
  File "/usr/lib/python2.5/socket.py", line 346, in readline
    data = self._sock.recv(self._rbufsize)
socket.error: (104, 'Connection reset by peer')
net-responsibility-report[31576]: send_report.py called incorrectly. Here's its usage message:
net-responsibility-report[31576]: {'email_to': ['<my email>@gmail.com'], 'name': '<my name>', 'logfile': '/var/log/net-responsibility.log', 'smtp_server': {'use_tls': True, 'authentication': True, 'login_name': '<my email>@gmail.com', 'password': '<my password>', 'use_smtp': True, 'port': 465, 'server': 'smtp.gmail.com'}, 'pidfile': '/var/run/net-responsibility.pid', 'email_from': '<my email>@gmail.com'}
net-responsibility-report[31576]: {'use_tls': True, 'authentication': True, 'login_name': '<my email>@gmail.com', 'password': '<my password>', 'use_smtp': True, 'port': 465, 'server': 'smtp.gmail.com'}
net-responsibility-report[31576]:
net-responsibility-report[31576]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[31576]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[31576]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[31576]: => from /usr/local/bin/net-responsibility-report:102:in 'initialize'
net-responsibility-report[31576]: => from /usr/local/bin/net-responsibility-report:118:in 'new'
net-responsibility-report[31576]: => from /usr/local/bin/net-responsibility-report:118
/usr/share/net-responsibility/lib/report_mailer.rb:81:in `send_message': send_report.py called incorrectly (ArgumentError)
        from /usr/share/net-responsibility/lib/report_mailer.rb:91:in `create_and_send'
        from /usr/local/bin/net-responsibility-report:89:in `initialize'
        from /usr/local/bin/net-responsibility-report:118:in `new'
        from /usr/local/bin/net-responsibility-report:118

```

---

### Post by Pursuer on 2008-04-22
Okay, so I tried to get the experimental version through Terminal, but it said,>  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I have been getting that for anything I am trying to install, including a program to transfer music from my MP3 player or delete music... everything is coming up with that message. It wasn't before, so I am at a loss.

---

### Post by Pursuer on 2008-04-23
Well, I tried the sudo superuser command, and then tried to install net responsibility. I received this message:

> E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)


Do you know what missing arch there may be?

---

### Post by mssever on 2008-04-23
> **javajoe220 said:**
> I've tried out the new version and here are the results:

In a nutshell, GMail requires either port 465 or 587, 587 works but 465 produced an error.
Thanks for the report. I was able to duplicate it, but I don't know what's wrong. So I documented it in the configuration tool.

Your report also brought to light another bug where a transient network error could prevent the tool from running. That's fixed now.

I think I'll go ahead and do a release when I get the time (not today).
> **Pursuer said:**
> Okay, so I tried to get the experimental version through Terminal, but it said, >  			 				 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
I have been getting that for anything I am trying to install, including a program to transfer music from my MP3 player or delete music... everything is coming up with that message. It wasn't before, so I am at a loss.
It appears that the package manager died a horrible death at some point. This probably has nothing to do with Net Responsibility. Running the command the error message says to run will probably fix it.
> **Pursuer said:**
> Well, I tried the sudo superuser command, and then tried to install net responsibility. I received this message:
> E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)
Do you know what missing arch there may be?
That's probably the source of your problem. Either that Java package is messed up, something that uses it is messed up (Net Responsibility doesn't use any Java stuff), or you've got a messed up repository. If my suggestion above doesn't resolve your trouble, you should post a new thread about this so that those who know how to fix such problems will see it. Because, like I said, I'd be shocked if it had anything to do with Net Responsibility.

---

### Post by Pursuer on 2008-04-23
Thank you. I did not believe it had to do with N.R. either, as I was getting the first messed up message for music playing programs, and many others.
I am starting to really be annoyed with this.

---

### Post by Mattevt on 2008-05-02
My dad want's me to replace XP with Xubuntu on one of the house computers, in order to make it more efficient. However, all the computers in the house have Covenant Eyes installed and he wants to mantain some sort of accountability software on the machine.

Does this program work like Covenant Eyes?
Does it work in Xubuntu?

Thanks,
Matt

---

### Post by mssever on 2008-05-03
> **Mattevt said:**
> Does this program work like Covenant Eyes?I've never used Covenant Eyes, so I don't know.
> Does it work in Xubuntu?Presumably, it does. The main difference between the *buntus is the graphical user interface. And Net Responsibility works behind the scenes, without a graphical interface. I don't run Xubuntu, so I can't make any guarantees, but if you do have problems, bug reports are welcome. :)

---

### Post by dailychoices on 2008-05-06
It may be worth a look into Covenant Eyes. I use it on my windows boxes now. I'm also looking to move one or more OS's to Ubuntu from windows, but like Mattevt I would like to maintain accountability.

Covenant Eyes monitors internet traffic and produces a report for accountability partners, one of the things that makes it more valuable than a straight report is that it scores the urls and draws attention to "suspect" websites. This allows the accountability partners to see at a glance whether there is something they should follow up on.

Perhaps there is some way to integrate with Dan's Guardian and their intelligence in evaluating web sites and their content?

Let me know how I can help. I'm very interested in having and providing a service like this.

Thanks,
Jonathan

---

### Post by eric.duveau on 2008-05-06
> **dailychoices said:**
> 

Perhaps there is some way to integrate with Dan's Guardian and their intelligence in evaluating web sites and their content?

Let me know how I can help. I'm very interested in having and providing a service like this.

Thanks,
Jonathan

I have done something similar:

**1) configure postfix (used smarthost):**
sudo -s
dpkg-reconfigure postfix
test with:
mail -s testpostfix [email]youremail@yahoo.com[/email]
tail -f /var/log/mail.info
**2) monitoring process email dansguardian DENIED content**
sudo -s
crontab -l
*/1 *	* * * /usr/local/sbin/rtmon 

cat /usr/local/sbin/rtmon 
#!/bin/bash
cat /var/log/dansguardian/access.log | grep DENIED > /var/log/dansguardian/rt.log
longueur=`cat /var/log/dansguardian/rt.log | wc -l`
limite=5
if (("$longueur" >= "$limite")); then
  cat /var/log/dansguardian/rt.log | mail -s "Alert Monitoring for DUVEAU" [email]eric.duveau@9mail.com[/email]
cp /dev/null /var/log/dansguardian/access.log
fi

---

### Post by mssever on 2008-05-06
> **dailychoices said:**
> It may be worth a look into Covenant Eyes.Since I don't run Windows, I don't have any experience with Covenant Eyes. But feature suggestions (such as yours) are welcome. :)
> Let me know how I can help. I'm very interested in having and providing a service like this.
There are several things that would be really helpful. One is to read through this whole thread and add the unresolved bug reports and feature requests to the appropriate [Sourceforge tracker]("http://sourceforge.net/tracker/?group_id=205710"). If in doubt whether something is resoved, add it to the tracker. Copying and pasting should suffice. This thread is a poor way of keeping track of such things.

Another thing would be to implement some feature you want and send me a patch. This is the surest way to get new features. :)

A third thing would be to discover and post ways to get more (or more relevant) data. Currently, Net Responsibility is fairly limited in what it can log. On this subject, thanks to eric.duveau for demonstrating how to integrate Dansguardian. Last time I tried Dansguardian, I couldn't get it to work. Once I'm able to solve the issues keeping me from upgrading to Hardy, I'll check that out.

Finally, I'd like to start developing the web interface, which will greatly improve the usability of Net Responsibility. However, I don't have a host lined up. I plan to use Python and Django for the backend, and my current webhost is inadequate for that. I'd like to use Google App Engine, but I have no idea when they'll give me an account. So any solutions to this problem are welcome.

---

### Post by mssever on 2008-05-07
I've just released Net Responsibility 0.5.0. Finally! The most significant new feature is much improved e-mailing. You no longer have to mess with Postfix! See the release notes below for more details and additional changes.

If you're upgrading from a previous release, you need to re-run Applications > Internet > Configure Net Responsibility to update your config. If you don't do this right away, the result is undefined. And computers don't like undefined situations. :)

If you're currently running an SVN version, you have two options: Either update your SVN working copy and re-build, or uninstall before installing 0.5.0. The problem is that SVN's version numbers appear higher than the release, so APT won't upgrade you automatically.


** Release notes:**
```
Release 0.5.0:
 - Switched the SMTP portion to Python, gaining the ability to use
   standard SMTP to send mail via Gmail or a regular ISP's mail server.
   This also means that we no longer depend on Postfix, and avoids the
   most frequently-reported problem with Net Responsibility: Postfix
   misconfiguration.

 - We now send the report daily instead of weekly. Hopefully that will
   be more manageable. Of course, the ideal solution is a web service,
   but that isn't here yet.

 - Better debugging has been in SVN for a while. Now it's available in
   the released version.

 - Several bugs sometimes prevented logfile pruning, especially when
   the file was large. And an unpruned logfile grows large quickly.
   This would eventually crash Net Responsibility. Those bugs have been
   squashed. Hopefully there are no more.
```

---

### Post by volleybounce on 2008-05-08
Hi!  I know nothing about computers and I don't know if I'm asking this in the right place but would appreciate some guidance/direction/help please, if possible.  I found this thread in regards to your comments about Covenanteyes.  My husband has it on his computer, because he needs it and he is very computer savy.  He has a successful website of his own.  I feel that if Covenanteyes can be circumvented he could figure out how to do it.  I am one of his accountability partners and I am seeing something that makes me think he has figured out how to circumvent.  Would any of you be able to discuss this possibility with me?

---

### Post by mssever on 2008-05-08
> **volleybounce said:**
> Hi!  I know nothing about computers and I don't know if I'm asking this in the right place but would appreciate some guidance/direction/help please, if possible.  I found this thread in regards to your comments about Covenanteyes.  My husband has it on his computer, because he needs it and he is very computer savy.  He has a successful website of his own.  I feel that if Covenanteyes can be circumvented he could figure out how to do it.  I am one of his accountability partners and I am seeing something that makes me think he has figured out how to circumvent.  Would any of you be able to discuss this possibility with me?

The best place to ask about Covenant Eyes is on a Covenant Eyes forum. Nevertheless, here's what I know. I don't think that there's such a thing as software that can't be circumvented by someone sufficiently skilled and determined. The way Net Responsibility works, though, is if someone circumvented it, you would either see shutdown notices in the report, or you would stop receiving reports. Of course, even that could be circumvented by someone sufficiently skilled and determined, though I don't want to publicly explain ow to do it.

I don't know how much of what I've said is relevant to Covenant Eyes, though.

---

### Post by dailychoices on 2008-05-08
> **volleybounce said:**
> I feel that if Covenanteyes can be circumvented he could figure out how to do it.  I am one of his accountability partners and I am seeing something that makes me think he has figured out how to circumvent.  Would any of you be able to discuss this possibility with me?

May I ask what you are seeing that is making you think he has figured out a way around it? It would help in determining if you are seeing something that shouldn't be happening.

In my experience, if CovenantEyes is shut down prematurely a notice will be sent out in the reports. Sometimes this is caused by Windows crashing or hanging and they have to reboot the computer, but that shouldn't happen very often. The other indicator I could see showing up in the reports is odd gaps in time between activity in the reports.

I have an outside theory as to how it might be circumvented, though I haven't tried it myself. But by doing so it would stop tracking any activity, either causing gaps in the report time lines or you will stop receiving reports all together.

Jonathan

---

### Post by volleybounce on 2008-05-08
Hi guys or girlfriends?  Thanks for helping me out.  I will try to find a Covenant Eyes forrum, I haven't looked yet.  I just stumbled onto you guys and thought you sounded savy to these matters.  I did not want to post what I am seeing on this board but would rather discuss all this behind the scenes so as not to teach anyone how to do it, as mssever stated as well.  

You can request to be my friend but I don't think I'm allowed to use the "chatting" system until I have 75 posts, which will never happen.  So I don't really know how to get the info I need without advertising on the world-wide-web how to circumvent.  Is there a way?

---

### Post by volleybounce on 2008-05-08
I suppose I could ask, do the words linux and red hat mean anything to you?  If not, there are other things I am seeing that need answered.  I was just curious about those two.

Also, I'm having a hard time finding a forum with guys like you with knowledge concerning CE. Do you know of one?

---

### Post by mssever on 2008-05-08
> **volleybounce said:**
> I did not want to post what I am seeing on this board but would rather discuss all this behind the scenes so as not to teach anyone how to do it, as mssever stated as well.  

You can request to be my friend but I don't think I'm allowed to use the "chatting" system until I have 75 posts, which will never happen.  So I don't really know how to get the info I need without advertising on the world-wide-web how to circumvent.  Is there a way?If you'd like to send me a private message, I'd be happy to discuss the non-public matters there, although as I said before, I have no experience with Covenant Eyes. Normally, I don't like to carry out discussions via private message, preferring instead to keep them public, but this is an exception.

I'm pretty sure there's no minimum post count before you can use private messages. If there is, let me know and I'll give you my e-mail address.
> **volleybounce said:**
> I suppose I could ask, do the words linux and red hat mean anything to you?  If not, there are other things I am seeing that need answered.  I was just curious about those two.This forum is mainly focused on the Ubuntu distribution of Linux. Red Hat is another distribution. So yes, most of us here know something about Linux.

Think of Linux being like your computer. Then the various distributions (such as Ubuntu and Red Hat) are like different brands of computer (such as Dell and HP). Net Responsibility, the program that's the subject of this thread, is specifically for Linux.

> Also, I'm having a hard time finding a forum with guys like you with knowledge concerning CE. Do you know of one?
CE stands for different things to different people. What do you mean by CE? Ubuntu Christian Edition?

---

### Post by mssever on 2008-05-08
I received a message via private message. I'm pasting my reply (which quotes the original in its entirety) here for the record.
> **mssever]Thanks for contacting me. In the future, though, please post in the forum thread said:**
> I noticed you wanted to make a way for your application to be hard to kill. What if the installer added a line to the inet startup daemon that ran a hidden binary in /usr/bin at startup? The name of the process would be something that sounded like a system process.Hiding the process would be difficult, because no matter what I name it, it will show up in the process list prefixed by ruby (the interpreter). Since the average user won't have many other Ruby programs installed (this could easily be the only one), the ruby prefix would be a giveaway. So unless I wanted to alter Ruby itself, I couldn't remove Ruby from the process list. Furthermore, trying to hide the process will only create suspicion; open source software does everything out in the open. The solution I'm looking for is determining whether the user explicitly killed Net Responsibility, or whether it exited due to system shutdown. I'm not interested in preventing the user from killing it, because that's impossible in Linux. The point is, that if the accountability partner sees that Net Responsibility has been killed, they should ask some questions.

Basically, the Linux world operates very differently from the Windows world.

> One way you could get the application to not send a large amount of URLs every report would be to use a keylogger solution instead. It would log all keystrokes, and the report mailer would then grep keywords out. "porn," "girl," "sex," "suicidegirls," etc. would show up in the report, but not the chap's credit card number!A keylogger would have its uses, but it would do nothing to detect someone who clicked links, opened bookmarks, etc. A keylogger would be no substitute for real accountability software. However, integration with Dansguardian might be beneficial.

> One thing to keep in mind is that you will need a way to email the reports. Unless you can find an open SMTP server to route the report through, you will have to run an SMTP daemon on the computer. The user could then simply shut down the mail daemon, and no report would be sent. Unless I'm totally mistaken, and you already have a way in mind.That was true until the latest release (0.5.0). Now, Net Responsibility can connect to a remote SMTP server, such as Gmail or the user's ISP's SMTP server. Additionally, if a report is missing, that should raise questions for the accountability partner about why they aren't receiving reports.[/quote]

---

### Post by volleybounce on 2008-05-09
Hi mssever.  I tried to pm you and it still says that I must have posted 75 times before I can use that feature. However, someone else emailed me concerning this so you could email me too.  I would like to see what both of you think, if possible.  Thanks for your time and help!!!!

HA! I'm not computer savy enough to use abbreviations like that. CE to me, means Covenant Eyes!

---

### Post by eric.duveau on 2008-05-11
> **mssever said:**
> I've been working on an Internet accountability program for Linux. The idea is to log the websites you visit, then periodically e-mail that log so someone else. It also writes a log entry when it is shutdown.

I'm looking for people to test it. Any comments (or code contributions) are welcome.

Still to do:
[LIST]
[*]Make a configuration GUI (partially completed, but on hold for now)
[*]Increase the intelligence of the shutdown logger
[*]Build a web service that will provide a friendlier, configurable way for the accountability partner to view the logs
[/LIST]
**Installation**
[I]
NOTE: I keep this post up to date, and it is the canonical place for installation instructions, usage, known bugs, etc. The discussion later in the thread often deals with specific issues and/or versions of Net Responsibility, so a given post might not contain current information.[/I]
[LIST=1]
[*]Download Net Responsibility. You can get the latest release from the [Sourceforge download page]("http://sourceforge.net/project/platformdownload.php?group_id=205710"). If you're feeling adventurous, you can use Subversion to check out the latest development version: ```
svn checkout https://responsibility.svn.sourceforge.net/svnroot/responsibility/trunk net-responsibility
```
[*]If you downloaded the .deb, simply install it. If you downloaded the source tarball, extract it and follow the directions in the README file.
[*]Run Applications > Internet > Configure Net Responsibility.
[/LIST]
[B]Running
[/B]
The core of Net Responsibility is a daemon that runs in the background. It is started automatically when you boot your computer. However, if you want to control it manually for testing purposes, here's how:
[LIST]
[*]Start ```
sudo net-responsibility-daemon
```
[*]Stop ```
sudo /etc/init.d/net-responsibility-daemon stop
```
[/LIST]
Net Accountability sends daily reports via e-mail. Be sure to set the proper e-mail addresses in the config file (/etc/net-responsibility.conf). The easiest way to accomplish this is by running Applications > Internet > Configure Net Responsibility. You can generate a report at any time by typing ```
sudo net-responsibility-report
```**Known Bugs**
Both net-responsibility-daemon and net-responsibility-report print an error message similar to the following to one or more of stderr, /var/log/syslog, or /var/log/daemon.log:```
net-responsibility-report[17580]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[17580]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[17580]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:153:in 'close'
net-responsibility-report[17580]: => from /usr/local/bin/net-responsibility-report:100:in 'initialize'
net-responsibility-report[17580]: => from /usr/local/bin/net-responsibility-report:116:in 'new'
net-responsibility-report[17580]: => from /usr/local/bin/net-responsibility-report:116
``` (The process name and ID vary, of course.) I haven't been able to solve this error yet, but I don't think that it's serious. Previously, I suppressed it, but I'm not comfortable with suppressing error messages.


For those who are ready to invest some money to make the double job of filtering and monitoring, 

here are 2 routers that seems be very effective in content filtering + accountability (monitoring by a partner or parent) 

**ZyWALL 2WG** _[http://www.zyxel.com]("http://www.zyxel.com")_ **iphantom** _[http://residential.iphantom.com/]("http://residential.iphantom.com/")_ 

**ZyWALL 2WG: ~$200 + ~$70 per year** [LIST] [*]very accurate url database (Bluecoat.com) [*]real time alerting when blocked sites are accessed _[page 479 of the user guide]("http://www.zyxel.com/web/support_download_list.php?indexflag=20040906173729&ModelIndexflags=0,420060717102012#")_ [/LIST] **iphantom: ~$129.95 + ~$59.95 per year** [LIST] [*]cheaper [*]easier to configure [/LIST]

---

### Post by valyok on 2008-05-20
> **mssever said:**
> I received a message via private message. I'm pasting my reply (which quotes the original in its entirety) here for the record.
As to emailing the report using SMTP servers - how in the world will that work if SMTP servers require authorization? 
When I run the config for the program I only set up the server name and port but not the account user name and password.
Or am I missing something?

Thnx!

---

### Post by mssever on 2008-05-21
> **valyok said:**
> As to emailing the report using SMTP servers - how in the world will that work if SMTP servers require authorization? 
When I run the config for the program I only set up the server name and port but not the account user name and password.
Or am I missing something?

Thnx!
What version are you running? You can type ```
net-responsibility-daemon --version
``` to find out. I suspect that you aren't using the latest version, because unless I goofed big time, the config program should ask you for your username and password. I'm currently sending via Gmail and it works for me.

---

### Post by valyok on 2008-05-27
> **mssever said:**
> What version are you running? You can type ```
net-responsibility-daemon --version
``` to find out. I suspect that you aren't using the latest version, because unless I goofed big time, the config program should ask you for your username and password. I'm currently sending via Gmail and it works for me.
Thnx a lot! For some reason I thought I was using version 0.5, but it was 0.4.3

So I configured the mail server settings and now test it. Shouldn't it fire an email as soon as you add one to the list and config the settings?

Thnx!

---

### Post by mssever on 2008-05-28
> **valyok said:**
> Thnx a lot! For some reason I thought I was using version 0.5, but it was 0.4.3

So I configured the mail server settings and now test it. Shouldn't it fire an email as soon as you add one to the list and config the settings?

Thnx!
I've never thought of automatically sending a test e-mail. Perhaps the config program should ask if it should send a test e-mail.

You can test your settings by running ```
sudo net-responsibility-report
``` Add the --debug option if you want to see all the gory details. Note that every time you generate a report, the report tool cleans the logfile, so if you run it multiple times, you could get a blank report if nothing has happened since the last time your ran the report.

---

### Post by MemphisJones on 2008-05-28
Thank you for this needed app.  This is my first foray into anything Linux, and an accountability application was one of the first things I looked to install.  I installed Hardy on my G3 iBook 800 (PPC) and then tried to install you deb package.  My package installer gave me an error about wrong architecture and I saw that someone else had this same problem and you suggested they download the source and build it.  Well it took me about a day or so to figure out how to do it but I did and now have 0.5.0 loaded and working (so far) on my machine!

---

### Post by mssever on 2008-05-29
> **MemphisJones said:**
> Thank you for this needed app.  This is my first foray into anything Linux, and an accountability application was one of the first things I looked to install.  I installed Hardy on my G3 iBook 800 (PPC) and then tried to install you deb package.  My package installer gave me an error about wrong architecture and I saw that someone else had this same problem and you suggested they download the source and build it.  Well it took me about a day or so to figure out how to do it but I did and now have 0.5.0 loaded and working (so far) on my machine!
If I can ever make sufficient sense out of .deb packaging, I'll switch to a proper package. Yours is one of several problems with my .debs. Net Responsibility is 100% platform-independent, so the .deb should be built that way. Unfortunately, my current build system doesn't seem to allow that.

---

### Post by brandroid on 2008-06-14
First off, thanks very much for creating an app like this for Linux.

However, I can't seem to get it to send out the reports. When I tell it to genrerate a report, I get this:

net-responsibility-report[16908]: Generating report
net-responsibility-report[16908]: Sending report
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 69, in <module>
    s = smtplib.SMTP(smtpinfo['server'], smtpinfo['port'])
  File "/usr/lib/python2.5/smtplib.py", line 244, in __init__
    (code, msg) = self.connect(host, port)
  File "/usr/lib/python2.5/smtplib.py", line 310, in connect
    raise socket.error, msg
socket.error: (110, 'Connection timed out')
net-responsibility-report[16908]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[16908]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[16908]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[16908]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[16908]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[16908]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/report_mailer.rb:83:in `send_message': send-report.py exited due to an unhandled exception. (RuntimeError)
	from /usr/share/net-responsibility/lib/report_mailer.rb:93:in `create_and_send'
	from /usr/local/bin/net-responsibility-report:89:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119



Also, it sat for about a half hour at the "sending report" line.

My email address is correct, the addresses being sent to are accurate, my mail server is "stmp.gmail.com", the port is 587, authentication is yes, login name is my email address without the @gmail.com, my password is correct, and TLS is yes.

Any clues how to get this to work? Thanks for all your help, in advance.

---

### Post by mssever on 2008-06-16
> **brandroid said:**
> Any clues how to get this to work? Thanks for all your help, in advance.
Have you tried this a second time? The error you posted suggests that you were probably experiencing network trouble when you tried to mail out the report. I've got a fix mostly completed that will give a more-useful error message.

Still, try again and it'll probably work. If not, then run the report with the --debug flag: ```
sudo net-responsibility-report --debug
``` and post the output. **Warning: using the --debug flag will cause it to print out sensitive information such as your password and all e-mail addresses it knows about--possibly multiple times. Be sure to sanitize the output before posting it.**

Also, when you post blocks of output, it's much easier to read if you put it in [noparse]```

```[/noparse] tags.

---

### Post by brandroid on 2008-06-16
I've tried multiples times, and each time I get the same result.

And I can't promise that this is all the debug had to say. As I scrolled up, I saw this same group of lines (from "debugging information" to "end") repeated many times. So many times, in fact, that I couldn't go back far enough to see where I originally had entered in the command.

```

net-responsibility-report[14065]: ---------- Debugging Information ----------
net-responsibility-report[14065]: File: /usr/share/net-responsibility/lib/modules/db.rb
net-responsibility-report[14065]: Line: 160
net-responsibility-report[14065]: Object class: SQLite3::ResultSet
net-responsibility-report[14065]: #<SQLite3::ResultSet:0xb68fb658 @stmt=#<SQLite3::Statement:0xb690fff4 @results=#<SQLite3::ResultSet:0xb68fb658 ...>, @db=#<SQLite3::Database:0xb7b7fef0 @type_translation=false, @results_as_hash=false, @driver=#<SQLite3::Driver::Native::Driver:0xb7b76b48 @authorizer={}, @callback_data={}, @trace={}, @busy_handler={}>, @transaction_active=false, @closed=false, @handle=#<SWIG::TYPE_p_sqlite3:0xb7b76abc>, @translator=nil, @statement_factory=SQLite3::Statement>, @driver=#<SQLite3::Driver::Native::Driver:0xb7b76b48 @authorizer={}, @callback_data={}, @trace={}, @busy_handler={}>, @types=[nil], @remainder="", @closed=false, @handle=#<SWIG::TYPE_p_sqlite3_stmt:0xb68fb248>, @columns=["count()"]>, @db=#<SQLite3::Database:0xb7b7fef0 @type_translation=false, @results_as_hash=false, @driver=#<SQLite3::Driver::Native::Driver:0xb7b76b48 @authorizer={}, @callback_data={}, @trace={}, @busy_handler={}>, @transaction_active=false, @closed=false, @handle=#<SWIG::TYPE_p_sqlite3:0xb7b76abc>, @translator=nil, @statement_factory=SQL
net-responsibility-report[14065]: ite3::Statement>, @driver=#<SQLite3::Driver::Native::Driver:0xb7b76b48 @authorizer={}, @callback_data={}, @trace={}, @busy_handler={}>, @eof=true, @first_row=false>
net-responsibility-report[14065]: <<<<< End >>>>>
net-responsibility-report[14065]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[14065]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[14065]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[14065]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[14065]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[14065]: => from /usr/local/bin/net-responsibility-report:119

```

---

### Post by izak on 2008-06-18
Wow, this looks software is exactly what I am looking for. Thank you!

However, I can't get it installed:(. I run amd64 version of ubuntu hardy. I downloaded the newest source files and built the deb according to instructions. It creates a subdirectory 'linux-2.6-x86_64' and when I try to install the deb located there, I get an error "Error: wrong architecture x86_64".

Is it possible for me to use this software? I thought building from source should make it platform independent?

---

### Post by brandroid on 2008-06-24
I tried running the debug again (but this time I increased the amount of scrollback) and there something new

```

net-responsibility-report[16970]: ---------- Debugging Information ----------
net-responsibility-report[16970]: File: /usr/share/net-responsibility/lib/modules/db.rb
net-responsibility-report[16970]: Line: 250
net-responsibility-report[16970]: Object class: SQLite3::ResultSet
net-responsibility-report[16970]: #<SQLite3::ResultSet:0xb66416b0 @stmt=#<SQLite3::Statement:0xb6641714 @results=#<SQLite3::ResultSet:0xb66416b0 ...>, @db=#<SQLite3::Database:0xb7c01f18 @type_translation=false, @results_as_hash=false, @driver=#<SQLite3::Driver::Native::Driver:0xb7bf8b70 @authorizer={}, @callback_data={}, @trace={}, @busy_handler={}>, @transaction_active=false, @closed=false, @handle=#<SWIG::TYPE_p_sqlite3:0xb7bf8ae4>, @translator=nil, @statement_factory=SQLite3::Statement>, @driver=#<SQLite3::Driver::Native::Driver:0xb7bf8b70 @authorizer={}, @callback_data={}, @trace={}, @busy_handler={}>, @remainder="", @closed=false, @handle=#<SWIG::TYPE_p_sqlite3_stmt:0xb6641674>, @columns=nil>, @db=#<SQLite3::Database:0xb7c01f18 @type_translation=false, @results_as_hash=false, @driver=#<SQLite3::Driver::Native::Driver:0xb7bf8b70 @authorizer={}, @callback_data={}, @trace={}, @busy_handler={}>, @transaction_active=false, @closed=false, @handle=#<SWIG::TYPE_p_sqlite3:0xb7bf8ae4>, @translator=nil, @statement_factory=SQLite3::Statement>, @dri
net-responsibility-report[16970]: ver=#<SQLite3::Driver::Native::Driver:0xb7bf8b70 @authorizer={}, @callback_data={}, @trace={}, @busy_handler={}>, @eof=true, @first_row=true>
net-responsibility-report[16970]: <<<<< End >>>>>

```

at the same time, this also appeared
```

["16371"], ["16372"], ["16373"], ["16374"], ["16375"], ["16376"], ["16377"], ["16378"], ["16379"], ["16380"], ["16381"], ["16382"], ["16383"], ["16384"], ["16385"], ["16386"], ["16387"], ["16388"], ["16389"], ["16390"], ["16391"], ["16392"], ["16393"], ["16394"], ["16395"], ["16396"], ["16397"], ["16398"], ["16399"], ["16400"], ["16401"], ["16402"], ["16403"], ["16404"], ["16405"], ["16406"], ["16407"], ["16408"], ["16409"], ["16410"], ["16411"], ["16412"], ["16413"], ["16414"], ["16415"], ["16416"], ["16417"]]

```
The scrollback settings weren't enough to catch where the numbers began, but it was at least 16145...if not something way before that.

---

### Post by martinquested on 2008-06-28
Brandroid, even though you normally login to gmail by typing your username without the trailing '@gmail.com', for SMTP you must include this.  So, if you are still not having any joy, have you tried adding the @gmail.com to your username yet?

---

### Post by martinquested on 2008-06-28
mssever, this is fantastic work - thank you!

Here's an idea for one way to streamline the reports, since they will clearly get very large very quickly.  The person receiving the report will soon be able to compile a long list of sites which s/he knows are safe - s/he will not wish to be told about these every day!

It would be great if the following scenario could work:
- my accountability partner (AP) compiles list of 'safe' sites
- my AP uploads list (e.g. by ftp) to a location on the web to which I have no write access
- Net Responsibility (NR) checks its report against the uploaded list and excludes all sites on that list from its report (length of report is potentially drastically reduced)
- NR includes in its report a confirmation that it has checked against an uploaded list, and confirms its URL
- NR mails report to AP
- AP checks that list URL is correct, and views remaining sites
- AP updates list periodically if necessary and uploads it by ftp again

Is this too complex?  Could it be a way of making the report manageable and hence more useful?  Otherwise, if I bombard my AP with long reports, he'll give up reading them, and I'll know it.

---

### Post by martinquested on 2008-06-28
One more thing: a bug, this time.

Running the report manually when there is nothing to report, appears to make the urlsnarf and ruby processes die, so that web usage after the report is sent is not monitored.  Does anyone else experience this?

---

### Post by brandroid on 2008-06-28
martinquested: thanks, but it didn't work.




I think my problem lies in the ports. Despite the fact that I can access gmail, and thunderbird can access gmail (and send messages via the stmp server), I think that the ports necessary for this are blocked. Since I live in what is essentially a college dorm, most ports are blocked. Could I be right with this, or am I completely off?

---

### Post by mssever on 2008-06-29
Sorry I haven't responded lately. I've been tied up with computer problems.

> **brandroid said:**
> And I can't promise that this is all the debug had to say. As I scrolled up, I saw this same group of lines (from "debugging information" to "end") repeated many times. So many times, in fact, that I couldn't go back far enough to see where I originally had entered in the command.
Yes, there's a ton of debugging information. Try something like this to capture it and save it to a file (which you'll need to sanitize to remove email addresses and your password before posting, ideally as an attachment): ```
sudo net-responsibility-report --debug > net-responsibility-log 2>&1
``` Note that the log will likely end up owned by root, so you'll have to use sudo when you're ready to delete it. You can call your logfile whatever you like.

Note that this is unnecessary in case your problem is ports.
> **brandroid said:**
> I think my problem lies in the ports. Despite the fact that I can access gmail, and thunderbird can access gmail (and send messages via the stmp server), I think that the ports necessary for this are blocked. Since I live in what is essentially a college dorm, most ports are blocked. Could I be right with this, or am I completely off?
That's possible, though the fact that Thunderbird can access Gmail causes questions. It's easy enough to test, though, using telnet.

This tries to establish a connection to smtp.gmail.com on port 587:
```
telnet smtp.gmail.com 587
```
If you get connected, see if the server will respond (I would use HELO scott-laptop.mss):
```
HELO your-domain.com
```
If you get a response that looks like this "250 mx.google.com at your service" then you can access the required port.
> **izak said:**
> However, I can't get it installed:(. I run amd64 version of ubuntu hardy. I downloaded the newest source files and built the deb according to instructions. It creates a subdirectory 'linux-2.6-x86_64' and when I try to install the deb located there, I get an error "Error: wrong architecture x86_64".

Is it possible for me to use this software? I thought building from source should make it platform independent?
Someone else posted a similar issue. Sometime, I need to switch to real packaging, because it's silly for epm to build platform-dependant packages when net-responsibility is platform-independant. The trouble is, I've never found documentation on building real .deb packages that I can understand. I'd suggest trying again.

Additionally, if you're willing to do some manual labor, you can manually install Net Responsibility. If you look at the file netresponsibility.list that gets created when you run ./configure_packages, it has complete instructions in epm format.

[LIST]
[*]Lines beginning with %requires are dependencies you need to install.
[*]Lines beginning with d are directories to create. The permissions and ownership are listed.
[*]Lines beginning with f show where to copy files (with appropriate ownership and permissions). The destination is listed first, and the source is last.
[*]Treat lines beginning with c as if they began with f.
[*]Lines beginning with l are symlinks to create.
[*]Lines beginning with i show how to arrange for net-responsibility-daemon to be started at boot.
[/LIST]
 > **martinquested said:**
> Here's an idea for one way to streamline the reports, since they will clearly get very large very quickly.  The person receiving the report will soon be able to compile a long list of sites which s/he knows are safe - s/he will not wish to be told about these every day!

It would be great if the following scenario could work:
- my accountability partner (AP) compiles list of 'safe' sites
- my AP uploads list (e.g. by ftp) to a location on the web to which I have no write access
- Net Responsibility (NR) checks its report against the uploaded list and excludes all sites on that list from its report (length of report is potentially drastically reduced)
- NR includes in its report a confirmation that it has checked against an uploaded list, and confirms its URL
- NR mails report to AP
- AP checks that list URL is correct, and views remaining sites
- AP updates list periodically if necessary and uploads it by ftp again

Is this too complex?  Could it be a way of making the report manageable and hence more useful?  Otherwise, if I bombard my AP with long reports, he'll give up reading them, and I'll know it.
Yes, something along these lines is in the works, although the goal is for it to be even more streamlined than what you suggested.
> **martinquested said:**
> Running the report manually when there is nothing to report, appears to make the urlsnarf and ruby processes die, so that web usage after the report is sent is not monitored.  Does anyone else experience this?
If you could get the crash message, it would help determine what the problem is. Look in /var/log/syslog for errors: ```
grep net-responsibility /var/log/syslog | less
```

---

### Post by brandroid on 2008-06-29
> If you get a response that looks like this "250 mx.google.com at your service" then you can access the required port.

I did what you said, and I did get that response.

> sudo net-responsibility-report --debug > net-responsibility-log 2>&1

I did that, as well, and I attached the log to this post.

edit: I forgot to mention that I used email1, email2, mypassword, and brandroid to replace the first addresss to be sent to/my address, the second address to be sent to, my password, and my username, respectively.

---

### Post by martinquested on 2008-06-29
As requested ,but there doesn't seem to be a crash report:
```

Jun 29 23:00:26 MQlaptop-kubuntu /etc/init.d/net-responsibility-daemon: Starting net-responsibility-daemon
Jun 29 23:00:28 MQlaptop-kubuntu net-responsibility-daemon[6625]: Starting
Jun 29 23:20:26 MQlaptop-kubuntu net-responsibility-report[12311]: Generating report
Jun 29 23:20:28 MQlaptop-kubuntu net-responsibility-report[12311]: Sending report
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-report[12311]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-report[12311]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-report[12311]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-report[12311]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-report[12311]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-report[12311]: => from /usr/local/bin/net-responsibility-report:119
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-daemon[6625]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-daemon[6625]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-daemon[6625]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-daemon[6625]: => from /usr/share/net-responsibility/lib/logger.rb:111:in 'run'
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-daemon[6625]: => from /usr/local/bin/net-responsibility-daemon:118:in 'initialize'
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-daemon[6625]: => from /usr/local/bin/net-responsibility-daemon:115:in 'loop'
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-daemon[6625]: => from /usr/local/bin/net-responsibility-daemon:115:in 'initialize'
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-daemon[6625]: => from /usr/local/bin/net-responsibility-daemon:152:in 'new'
Jun 29 23:21:11 MQlaptop-kubuntu net-responsibility-daemon[6625]: => from /usr/local/bin/net-responsibility-daemon:152

```

---

### Post by mssever on 2008-07-01
> **brandroid said:**
> I did that, as well, and I attached the log to this post.Well, it looks like you're experiencing several issues. The most immediate issue, which is keeping you from sending mail, is that your connection is timing out. Sometimes, it's being refused, instead. I'm not sure what's causing that for sure. How big is the file /var/log/net-responsibility.log? I'm wondering if maybe it's grown so big by now (since you've been having these problems for a while) that Gmail is rejecting it. You could, of course, stop Net Responsibility, delete or rename your logfile, and restart Net Responsibility. Then, with a small file, you can see if you can send then.

It also appears that there's some bug that's making Net Responsibility a) log data incorrectly, and b) attempt to rotate the log when it shouldn't. I've made a few changes to log more details. Would you mind copying the attached files over the ones in /usr/share/net-responsibility/lib (make sure you're running the latest release first), then re-getting the debugging output like you just did? I've added some additional debugging logs to help me better see what's happening.

P.S.: The replacement files just might fix the problem of the logs being rotated improperly.

> **martinquested said:**
> As requested ,but there doesn't seem to be a crash report:Hmm... It appears that you're getting some non-standard exception, which demonstrated a bug in my crash logger. Open /usr/share/net-responsibility/net-responsibility-daemon and replace this line (around line 140): ```
rescue StandardError, SQLite3::BusyException => error
``` with this one: ```
rescue Object => error #We want to rescue ALL POSSIBLE exceptions here.
``` Then, please try again, after restarting net-responsibility-daemon.

---

### Post by brandroid on 2008-07-02
> How big is the file /var/log/net-responsibility.log?

I don't think that's the problem. The log is only a couple of megabytes, and gmail is supposed to handle around 8-10MB.

> Would you mind copying the attached files over the ones in /usr/share/net-responsibility/lib (make sure you're running the latest release first), then re-getting the debugging output like you just did?

I did that, and it didn't fix the problem. I'm pretty sure I copied them over correctly, though I didn't know how to stop net-responsibility (and I'd rather not know since that would make it easier to get around once it does stop working), so I just sudoed nautilus and copied over the files, then restarted my computer.
I attached the log file.

---

### Post by mssever on 2008-07-03
> **brandroid said:**
> I don't think that's the problem. The log is only a couple of megabytes, and gmail is supposed to handle around 8-10MB.So we can rule that out, then. What is clear, though, is that your connection is timing out. For example, from the file you posted:
```
net-responsibility-report[8499]: counter = 0
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (110, 'Connection timed out')
net-responsibility-report[8499]: counter = 1
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (110, 'Connection timed out')
net-responsibility-report[8499]: counter = 2
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (110, 'Connection timed out')
net-responsibility-report[8499]: counter = 3
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (110, 'Connection timed out')
net-responsibility-report[8499]: counter = 4
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (110, 'Connection timed out')
net-responsibility-report[8499]: counter = 5
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (110, 'Connection timed out')
net-responsibility-report[8499]: counter = 6
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (111, 'Connection refused')
net-responsibility-report[8499]: counter = 7
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (110, 'Connection timed out')
net-responsibility-report[8499]: counter = 8
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (110, 'Connection timed out')
net-responsibility-report[8499]: counter = 9
net-responsibility-report[8499]: <class 'socket.error'>
net-responsibility-report[8499]: (110, 'Connection timed out')
net-responsibility-report[8499]: Unable to establish a connection to the SMTP server. Please check your network connection.
```This shows that Net Responsibility tried ten times to connect and got a timeout each time. I'd be foolish to say for certain that this isn't a problem with Net Responsibility, but it appears that it has something to do with your net connection. If there's something I can do to fix it, I don't know what that would be.

> I did that, and it didn't fix the problem. I'm pretty sure I copied them over correctly, though I didn't know how to stop net-responsibility (and I'd rather not know since that would make it easier to get around once it does stop working), so I just sudoed nautilus and copied over the files, then restarted my computer.
I attached the log file.Thanks for trying this. Something didn't happen right, because your log doesn't contain the information it should. I'm attaching a .deb with the changes. Try installing that, then re-run the debugging command.

Also, martinquested, I should have tested the code I gave you. It can cause problems. The attached .deb also contains debugging code for you.

---

### Post by brandroid on 2008-07-03
I had an error when I attempted to run the debug option with the new deb.

```
/usr/local/bin/net-responsibility-report:35:in `require': /usr/share/net-responsibility/lib/report_mailer.rb:72: syntax error, unexpected '}', expecting ')' (SyntaxError)
    Syslog.debug(:file => __FILE__, :line => __LINE__, :name => "send_report.py exit status", :obj => $?.exitstatus})
                                                                                                                    ^	from /usr/local/bin/net-responsibility-report:35
```

---

### Post by mssever on 2008-07-03
D'oh. Try this one.

---

### Post by brandroid on 2008-07-03
> Try this one. 

That's it. The new update got it to work. Thank you!!!

I was going to upload the debug file anyway, just in case it might help you. But then I noticed it also had the list of all the sites I've visited...so I'd rather not put that out on the internet. :P

I do have one more question though, and I don't remember if it was answered previously: how often does it send out reports?

edit: I re-ran the debug, and added that file (since all the sites were no longer on there).

---

### Post by mssever on 2008-07-03
> **brandroid said:**
> That's it. The new update got it to work. Thank you!!!

I was going to upload the debug file anyway, just in case it might help you. But then I noticed it also had the list of all the sites I've visited...so I'd rather not put that out on the internet. :P

I do have one more question though, and I don't remember if it was answered previously: how often does it send out reports?

edit: I re-ran the debug, and added that file (since all the sites were no longer on there).
I'm glad it's working. I just wish I knew what the problem was. Oh well. It sends reports daily.

For future reference, you could have simply deleted the list of sites you visited from the log; that wasn't important information. What mattered was that that information was present. So a note to that effect would have sufficed.

If you're still willing to help troubleshoot, you were experiencing another separate bug that should really be fixed. When sending the report failed, Net Responsibility was deleting the log data. But it should only do that on SUCCESS. Otherwise, it would be easy to game the data. If you're willing to try to send a report with your computer disconnected from the Internet (to simulate connection problems) and give me the debugging output, I'd like to look into that.

---

### Post by brandroid on 2008-07-03
> If you're willing to try to send a report with your computer disconnected from the Internet (to simulate connection problems) and give me the debugging output, I'd like to look into that.

okay, I did that. And the debug info is attached.

---

### Post by sinim on 2008-07-07
mssever, Is Net Responsibility easy enough for a total linux noob to install? I am using Ubuntu Hardy and have been following this thread for 10 months, very impressed with your guys dedication on this thing. Where can I find the deb file, and is there a place that has detailed instructions on setting it up? Thanks alot

Got it installed and configured but am getting this report in terminal 

net-responsibility-report[9878]: Generating report
net-responsibility-report[9878]: Sending report
send: 'ehlo [127.0.1.1]\r\n'
reply: '250-mx.google.com at your service, [125.34.70.64]\r\n'
reply: '250-SIZE 28311552\r\n'
reply: '250-8BITMIME\r\n'
reply: '250-STARTTLS\r\n'
reply: '250 ENHANCEDSTATUSCODES\r\n'
reply: retcode (250); Msg: mx.google.com at your service, [125.34.70.64]
SIZE 28311552
8BITMIME
STARTTLS
ENHANCEDSTATUSCODES
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 95, in <module>
    s.login(smtpinfo['login_name'], smtpinfo['password'])
  File "/usr/lib/python2.5/smtplib.py", line 554, in login
    raise SMTPException("SMTP AUTH extension not supported by server.")
smtplib.SMTPException: SMTP AUTH extension not supported by server.
net-responsibility-report[9878]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[9878]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[9878]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[9878]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[9878]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[9878]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/report_mailer.rb:86:in `send_message': send-report.py exited due to an unhandled exception. (RuntimeError)
	from /usr/share/net-responsibility/lib/report_mailer.rb:96:in `create_and_send'
	from /usr/local/bin/net-responsibility-report:89:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119

---

### Post by sinim on 2008-07-07
after reading your part on gmail, i tried using Securenym

I have installed and configured, and am trying to run through Securenym.com
My account settings are smtp.securenym.net with 465 as the port, once I generate the report it just hangs on "sending"

any ideas?

---

### Post by brandroid on 2008-07-13
So, after using this program for a little while, I'd like to make a feature request. I think it would be helpful if the program would send an email to the "accountability partners" when/if they've been removed from the list of email addresses. Just a thought...

---

### Post by mssever on 2008-07-14
> **sinim said:**
> Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 95, in <module>
    s.login(smtpinfo['login_name'], smtpinfo['password'])
  File "/usr/lib/python2.5/smtplib.py", line 554, in login
    raise SMTPException("SMTP AUTH extension not supported by server.")
smtplib.SMTPException: SMTP AUTH extension not supported by server.

It looks like your SMTP server doesn't support authentication.
> **sinim said:**
> after reading your part on gmail, i tried using Securenym

I have installed and configured, and am trying to run through Securenym.com
My account settings are smtp.securenym.net with 465 as the port, once I generate the report it just hangs on "sending"
It's possible that you're having some network trouble, or that you entered your mail server settings correctly. If, after checking that, you're still having trouble, please run the report in debugging mode: ```
sudo net-responsibility-report --debug 2>/tmp/report.log
```Then, post the log as an attachment. The log contains sensitive information such as your password and email addresses, so be sure to sanitize the log before posting it. A search and replace operation should be sufficient.
> **brandroid said:**
> So, after using this program for a little while, I'd like to make a feature request. I think it would be helpful if the program would send an email to the "accountability partners" when/if they've been removed from the list of email addresses. Just a thought...
That's a good idea. Implementing it in the current version of Net Responsibility would require a lot of thought. Since I'm about to begin work on the web service, I'll defer this feature until the web service is ready. In the mean time, if an accountability partner stopps receiving reports, he/she should wonder what's up and start asking questions.

---

### Post by prayerwarriorps139 on 2008-07-30
mssever,

I just wanted to say thank you for building this software.  I was just looking for something like this and it is exactly what I need.  It sounds like development has been going well.  I will let you know if I find anything you could add/change.

Thanks again and God Bless.

---

### Post by Afkpuz on 2008-08-03
I have a feature request.  I've used X3 watch and I'm not sure what kind of filtering they use, but the email reports do not show every website visited.  Instead, I think they just cross reference all visited sites with a list of naughty words that are often associated with porn.  That way, when the person being watched does not visit any pornographic sites, the accountability partner receives an empty email.  This makes it obvious right away to the accountability partner that there are no questionable sites visited and also prompts a call of congratulation to the friend.  So, would it be possible to filter the log file through a simple word search and only include the questionable sites?  I only say this because my friend whom I would like to send these reports to probably won't read through a long email, especially if it contains even a days worth of surfing.  Also, he is fairly computer illiterate, so the simpler, the better.

I'd be willing to help compile that list of key words to search if that would help.  

Also, another quick question.  How often do these reports get sent out?  Can I set it to send every 2 weeks?

Anyways, thanks for this software.  I was about to leave linux to go back to windows and X3 watch, but this saved the day!  Thanks a million

---

### Post by mssever on 2008-08-05
> **Afkpuz said:**
> Also, another quick question.  How often do these reports get sent out?  Can I set it to send every 2 weeks?
The reports are sent by anacron. There's a symlink for net-responsibility-report in /etc/cron.daily (older versions placed the symlink in /etc/cron.weekly) which--unsurprisingly--runs the report tool every day. You can set up a custom cron schedule if you want; but beware that if you run it too infrequently, the amount of data will be huge, which might cause the report to fail. The maximum interval depends on: how much you surf the Internet, how much RAM your system has, your SMTP server's maximum message size limit, the recipient's message size limit, and the recipient's willingness to sift through large messages.

Since you submitted a [feature request for your other question]("http://sourceforge.net/tracker/index.php?func=detail&aid=2037083&group_id=205710&atid=994739") (thanks for doing that!), I'll reply to that there. I'll only say here (since it's relevant to what I said in the lasp paragraph) that a web service is in the works which should be a major improvement on reporting.

---

### Post by McManmanel on 2008-08-07
I was searching for Linux-based accountability software and I stumbled onto this thread.  I have a comment/question.

First background: I am running a dual-boot installation on my laptop with WinXP and Ubuntu.  I am trying to switch to Ubuntu but one of the things holding me back is that there is not accountability software for Ubuntu.  So I applaud you for your efforts.  Thank you!  I use Covenant Eyes on my XP installation.  

I think Afkpuz is right in part that Covenant Eyes (and X3?) use a comparison with a keyword list.  I'm sure they also have a blacklist database and some other checks and balances.  I know Covenant Eyes at least has a scoring system that gives numerical scores to each website based on the probability that it is inappropriate.  So there is quite a bit of functionality and complexity built into the whole system at least for Covenant Eyes.  Another thing they do is that the accountability partner can see at a glance whether there are websites in the weekly report that need some looking into because each report has an overall score at the top, thus saving the accountability partner from having to read through a long, and probably mostly meaningless, list of URLs.  And the weekly report is a highlights/summary of web usage with more detailed, site-by-site information available on the Covenant Eyes website.

I don't know much about programming and even less about Ubuntu/Linux, but my question is: have you thought about the possibility that there could just be a Linux front-end that runs in Ubuntu and takes care of the logging of URLs, etc. plus some other functions (security, making sure the user can't bypass the service, etc.)  But then maybe the URL log data could be passed to a program like Covenant Eyes to take advantage of their well-developed URL scoring algorithms and reporting systems?  If it is possible, the advantage of that approach is that it would save "reinventing the wheel" with regard to all the things Covenant Eyes already does well (scoring, blacklist DB, etc).  And it would necessitate only developing a Linux compatible front-end to collect and pass data.  (Of course it would also require that Covenant Eyes be willing to partner with your front end, but I am only green-lighting here.)  Another great advantage would likely be that you could get a working beta much sooner to help Ubuntu users with accountability issues if they are willing to subscribe to Covenant Eyes.  And if you still want to develop a totally independent GNU-public license package, the Covenant Eyes partnership could be seen as a temporary or interim solution.  I'd be interested to know what your thoughts are on this.

---

### Post by mssever on 2008-08-08
> **McManmanel said:**
> I don't know much about programming and even less about Ubuntu/Linux, but my question is: have you thought about the possibility that there could just be a Linux front-end that runs in Ubuntu and takes care of the logging of URLs, etc. plus some other functions (security, making sure the user can't bypass the service, etc.)  But then maybe the URL log data could be passed to a program like Covenant Eyes to take advantage of their well-developed URL scoring algorithms and reporting systems?  If it is possible, the advantage of that approach is that it would save "reinventing the wheel" with regard to all the things Covenant Eyes already does well (scoring, blacklist DB, etc).  And it would necessitate only developing a Linux compatible front-end to collect and pass data.  (Of course it would also require that Covenant Eyes be willing to partner with your front end, but I am only green-lighting here.)  Another great advantage would likely be that you could get a working beta much sooner to help Ubuntu users with accountability issues if they are willing to subscribe to Covenant Eyes.  And if you still want to develop a totally independent GNU-public license package, the Covenant Eyes partnership could be seen as a temporary or interim solution.  I'd be interested to know what your thoughts are on this.
I don't know the technical details of how Covenant Eyes works. If CE logs websites locally, then sends them to a server somewhere, then making Net Responsibility work with CE wouldn't be too hard (provided the folks at CE are cooperative). From an open source standpoint, I think it would be great if Net Responsibility could work with several different service providers, possibly including both CE and X3.

If, however, CE works by setting the computer to contact a central proxy server, then supporting it would basically require a re-write. Arguably, a central proxy server is the best way to go, but it isn't something I could do unless I found a way to pay for it (it would require at least one dedicated server--probably several--and sufficient bandwidth to handle all my users' Internet traffic).

Suggestions are welcome. Hard facts and specific contributions are even more welcome.

---

### Post by xilix on 2008-09-27
It seems that there is not so much activity here. As this thread is still the website entered in the sourceforge project I conclude that there is not much happening with this project.

I think this is a very important project. As far as I know there is no other real choice for an accountability software for Linux.

Maybe there are other developers that can help if the main developer doesn't have the time?

---

### Post by Theophilosity on 2008-10-02
> **mssever said:**
> 
If, however, CE works by setting the computer to contact a central proxy server, then supporting it would basically require a re-write. Arguably, a central proxy server is the best way to go, but it isn't something I could do unless I found a way to pay for it (it would require at least one dedicated server--probably several--and sufficient bandwidth to handle all my users' Internet traffic).
Okay, as a Windows/CEyes user with some networking experience, I hope I can shed a little bit of light on this, but I'm open to the possibility that I'm wrong. I ran a tracert to google.com on my Vista laptop with CEyes installed and active. Tracert went to my router, then to IANA, then to Cox (my ISP), then to google, no stops between, as far as I can see. Now, I'm not sure how conclusive this is. If CEyes errors out, it still disables my internet until I reboot...but not my ICMP functionality. So, this may just be an example of that, but I suspect that the CEyes service running in the background is sending the log to CEyes' servers in realtime. Also, CEyes aims to not slow down your internet speed (and it doesn't), which it seems a proxy would do. I've emailed them to find out for sure, but wanted to give the best answer I could in the meantime.

---

### Post by mssever on 2008-10-03
One question about using traceroute. The Linux version works by sending either ICMP or UDP packets, which would bypass an HTTP proxy. Setting it to use tcp to port 80 on my box seeps to bypass all the intermediary steps (it hits my router, then google, whereas the default method takes 20 steps). I wonder if you'd have to inspect the actual outgoing packets to determine whether an HTTP proxy is in use.

---

### Post by Theophilosity on 2008-10-03
Yeah, i hear you, and I'm really not sure. However, I would expect that a proxy would cause significant downturn in performance, but I'm able to achieve locationally-appropriate speeds from home, work, etc. Also, I do know that whatever they're doing, it's occurring below the below my actual software...CEyes monitors all http traffic, as well as ftp, file sharing, and a host of other protocols. Hopefully they'll respond to my email.

---

### Post by linxlvr on 2008-10-04
I am sorry that I don't know how to code or anything, so I'm not really much help, but I do encourage you to work on this project. It would be a much needed addition to a CE Ubuntu, and linux in general.

Perhaps for a 'white list' it could refer to the Dan's Guardian lists, and if it fails that it could list the website?

Well, either way good luck with it!
-- 
dw

---

### Post by Theophilosity on 2008-10-06
forgive me for sounding like a nub. Is there a place that would help me locate the dependencies? I've tried everything, and got a couple of hard ones, but I still can't figure out how to get it to take the rpm. It still can't the dependencies. Here is the error text:
error: Failed dependencies:
	libdaemonize-ruby|libdaemons-ruby is needed by netresponsibility-0.5.0-0.i386
	libsqlite3-ruby is needed by netresponsibility-0.5.0-0.i386

I am trying to install using the rpm on fedora 8. Any help would be much appreciated. I already installed ruby daemons and ruby-sqlite3.

---

### Post by mssever on 2008-10-07
> **Theophilosity said:**
> forgive me for sounding like a nub. Is there a place that would help me locate the dependencies? I've tried everything, and got a couple of hard ones, but I still can't figure out how to get it to take the rpm. It still can't the dependencies. Here is the error text:
error: Failed dependencies:
    libdaemonize-ruby|libdaemons-ruby is needed by netresponsibility-0.5.0-0.i386
    libsqlite3-ruby is needed by netresponsibility-0.5.0-0.i386

I am trying to install using the rpm on fedora 8. Any help would be much appreciated. I already installed ruby daemons and ruby-sqlite3.
I haven't actually tested the RPM, as all my systems are in the Ubuntu family of distros (I ditched RedHat several years ago and haven't looked back). It's likely that some of the dependencies have different names in Fedora. You need to find the package name for Ruby's daemonize library and Ruby's sqlite3 library. When you find those names, you can adjust the dependencies in epm and rebuild. Or post them here and I'll help. Alternatevely, you can probably use alien to convert the .deb to an .rpm.

---

### Post by Theophilosity on 2008-10-07
I'm working on getting an Ubuntu install up-and-running so I can test. VirtualBox makes it all too easy. In the meantime, I had a random thought. Would it be even a right train of thought to eventually consider NetR as a kernel module, similar to SELinux or iptables? Obviously that would make it distro-specific, but it would seem to me that could make a big difference for admin-proofing it.

---

### Post by mssever on 2008-10-07
> **Theophilosity said:**
> I'm working on getting an Ubuntu install up-and-running so I can test. VirtualBox makes it all too easy. In the meantime, I had a random thought. Would it be even a right train of thought to eventually consider NetR as a kernel module, similar to SELinux or iptables? Obviously that would make it distro-specific, but it would seem to me that could make a big difference for admin-proofing it.
Yes, I recently discovered VirtualBox and I'm loving it. As far as a kernel module goes, that would definitely have some benefits, especially if it were compiled in instead of serving as a module (modules are easy to insert and remove at runtime). However, writing a kernel module is well beyond my current skill level. If someone else wants to do so, more power to them.

---

### Post by Theophilosity on 2008-10-21
So, just ftr, here is the email I received back from CovenantEyes:
> 
Thanks for contacting us, we do apologize for the delay. Covenant Eyes does not use a proxy, the software client logs into our servers in real-time. Let me know if you have further questions.

This really does seem like the best option, and in the same track you're already going: avoid a proxy, as it results in slowdown, but log to an off-site server in real-time. It seems like that could be added to NetR somewhere down the road.

Anyway, keep up the good work!

---

### Post by mssever on 2008-10-21
> **Theophilosity said:**
> log to an off-site server in real-time
Yes, but what does that mean? The CE e-mail said that they don't use a proxy, but they didn't explain what they mean by "logging on to a server in real time."

---

### Post by Theophilosity on 2008-10-22
As I understand it, the CEyes service/daemon running on my machine logs in the same way netfilter might log packets. These log entries are sent to CEyes log server in real-time. If the daemon/service can't connect to the log server, it simply blocks all packets (except icmp?) from my system processes. I don't know how it sorts what to log and what not to log, but this basically means I can't connect to anything without logging (which would be the case with a mandatory proxy), but the packets are not actually going through the CEyes server (which would be a nightmare). Let me know where I might be misunderstanding, or where there are holes in my explanation.

---

### Post by wildman4god on 2008-10-23
Hello,

     I have been following this project for some time now and I am glad that someone is taking the initiative to make an accountability software for Linux, (why x3 or CE doesn't do this is beyond me) but I have a suggestion for an option for people in restricted networks. I live at job corps who's network blocks all traffic except HTTP, so people can use proxies to still access bad content but netr can't use smtp to send the logs. My idea is that there's an add on for thunder bird that lets you access your web based mail through thunder bird with out imap or pop3 access. To make a long story short it routes mail through http rather than smtp using your yahoo or gmail, etc. account. If we could use this technology to allow netr to send the logs through our web based account this would allow the software to work on networks that block smtp traffic. I myself don't yet have the skills and knowledge to help with this so I am suggesting it to you but I hope i can someday help with the development of this software.

---

### Post by mssever on 2008-10-24
> **wildman4god said:**
> My idea is that there's an add on for thunder bird that lets you access your web based mail through thunder bird with out imap or pop3 access. To make a long story short it routes mail through http rather than smtp using your yahoo or gmail, etc. account. If we could use this technology to allow netr to send the logs through our web based account this would allow the software to work on networks that block smtp traffic.
That would require special-case behavior for every webmail provider. Essentially, it would involve writing a mini-automated browser that knew how to login and send mail. I'm surprised that some network would block SMTP entirely. I can see blocking most SMTP, but if you run a network, why not allow users to connect to your local SMTP server?

---

### Post by wildman4god on 2008-10-25
This add-on for thunder bird works with most web based mail servies (yahoo, gmail, hotmail, etc.) And as far as the network I am on blocking smtp traffic altogether, I am not sure why they do. I attend Pittsburgh Job Corps, which is a free education/training center set up by the department of labor to help disadvantaged people continue their education beyond high school. Anywho, being a part of the government they are paranoid about security so their response was to block all traffic except web traffic which for that they have a filter but it is easily by passed with a proxy. Other job corps centers around the usa let their students have access to more types of traffic probably because of their higher ranking, but our center and i am sure others are not ranked very well so we don't get as many privlages. all we can do is basic web surfing, we can't im or irc and we could use proxies for facebook and web based chats but when we do the interfaces don't work correctly. as is our motto "we have the internet we just can't use it." sorry for the long story, i just wanted you to know the situation and i thought it would be a simple matter to incoperate the code from the thunder bird add-on or to make a code the used thunder bird its self with the add-on as an option for those of us in a similar situation. I would like to help, but I have yet to learn how to code.

---

### Post by mssever on 2008-10-27
> **wildman4god said:**
> This add-on for thunder bird works with most web based mail servies (yahoo, gmail, hotmail, etc.)
Perhaps you can post the URL to the Thunderbird add-on you're referring to so I can take a look at it and see what it's doing.

---

### Post by wildman4god on 2008-10-27
[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by uncleclinto on 2008-11-02
Okay,

I need this thing to work if I'm going to be allowed to keep my Ubuntu install.  I've had it installed an running for a year now, with addys.  I've yet to see an email go out...  I've entered smtp servers and localhost on the email server line.  I've even installed postfix through package manager because I saw it in the thread somewhere.

Here's the deal.  I'm a desktop user.  I know a bit about web design and apache servers.  I like linux.  I'm not a programmer.  Where's the easy peasy howto on setting this thing up so emails my freaking accountability partner reliably??  Someone throw me a bone here!

---

### Post by shalamabobbi on 2008-11-09
I installed with no problem but the report doesn't get sent out. Also does the current version send an email out if the application is turned off/removed? or if the accountability partner's email is removed from the list? 

I think these 2 items are the most important.

You don't even need to log every site visited, you could simply randomly report sites being visited, sort of a russian roulette. The possibility of getting caught is enough for this type of accountability system to work.

Or if the same site is visited more than once it need only be logged once during any reporting period.

The report need only be sent out once every 2 weeks then deleted. 

problem areas are proxies, p2p content, usenets, etc. Maybe a thumnail collection log is what would better work? (or additionally). This would display any photos found on the hard drive or downloaded via any browser.
Maybe something that monitors any application that is used to view pictures whether on the hard drive, external HD, CD drive, usb thumbdrive, etc?

---

### Post by shalamabobbi on 2008-11-09
ok.. maybe a bug. 
i just installed ubuntu, so not sure. But the installation was stable and 
i had restarted the OS a few times, but after installing this application, my OS would not reboot. 

i got an orange screen after the password step and it hung there.

Anyhow more thoughts. The best solution is to have the isp that records everything anyways make the record available to view for those who want that accountability. You can always bypass this sort of software with a live CD etc. Even though it eliminates the immediate temptation for misuse it will not deture someone with any sort of determination to circumvent such a program.

---

### Post by mssever on 2008-11-09
> **shalamabobbi said:**
> I installed with no problem but the report doesn't get sent out. Also does the current version send an email out if the application is turned off/removed? or if the accountability partner's email is removed from the list?What happens if you run ```
sudo net-responsibility-report --debug
``` You can post the output if you like so I can take a look at it, but be sure to sanitize it, since it will contain sensitive information.

It should log/email if net-responsibility is turned off or uninstalled. However, I haven't figured out how to distinguish between killing it due to system shutdown, and someone manually killing it. Furthermore, I don't think it's possible log shutdowns in a way that can't be circumvented--though I suppose there could be some sort of periodic ping to prove the program's alive.

It doesn't log changes to the e-mail list, which is a bug.

> You don't even need to log every site visited, you could simply randomly report sites being visited, sort of a russian roulette. The possibility of getting caught is enough for this type of accountability system to work.I think it's better to have full data available.

> Or if the same site is visited more than once it need only be logged once during any reporting period.That would significantly reduce the length of the log. There are a couple of possibilities here. One is to only log (or at least report) a given URL once, another is to only report a given domain once. Maybe that could be a configurable setting. Less reporting would increase the usability of the report, but having full data available would probably still be important for some situations.

> The report need only be sent out once every 2 weeks then deleted.With abreviated reports, that might work. With the current situation, the e-mails would be far too long.

> problem areas are proxies, p2p content, usenets, etc. Maybe a thumnail collection log is what would better work? (or additionally). This would display any photos found on the hard drive or downloaded via any browser.
Maybe something that monitors any application that is used to view pictures whether on the hard drive, external HD, CD drive, usb thumbdrive, etc?Theoretically, proxies shouldn't affect Net Responsibility at all--though I haven't tested them to be sure. As far as the other items go, patches are welcome. Some of those would require a lot of work to implement, while others are stuff I really don't know how to effectively monitor.

> **shalamabobbi said:**
> ok.. maybe a bug. 
i just installed ubuntu, so not sure. But the installation was stable and 
i had restarted the OS a few times, but after installing this application, my OS would not reboot. 

i got an orange screen after the password step and it hung there.I don't think it's possible for Net Responsibility to cause such a problem. Do you have any kind of information to help track it down? Sometimes in cases like this ~/.xsession-errors contains helpful information (but it gets overwritten on every login or login attempt). Also, the various logs in /var/log often contain helpful information.

> Anyhow more thoughts. The best solution is to have the isp that records everything anyways make the record available to view for those who want that accountability. You can always bypass this sort of software with a live CD etc. Even though it eliminates the immediate temptation for misuse it will not deture someone with any sort of determination to circumvent such a program.
Doing this would, of course, require cooperation from the ISP. If ISPs were all cooperative in this--and suffeciently flexible to meet their users' varying needs--there would be no need for Net Responsibility. However, I doubt very many ISPs will be inclined to provide adequate filtering. Besides, Net Responsibility isn't filtering software--dansguardian already fills that niche. And if you can install dansguardian on your gateway, it can filter all your access. (One possible method would be to use a router with Linux-based firmware which allows you to install arbitraty software on it.)

---

### Post by shalamabobbi on 2008-11-10
I have decided to fore-go trying to use ubuntu at my home. I doubt that my issues with your software pose any new situations that you haven't come across already so I won't trouble you with getting me up and running. I will continue to use windows with X3 watch installed from home. The Linux had an issue with proprietary drivers for the motherboard which is why it is crashing I think. I will run it on another PC from work probably with an older version of SUSE since it is for a work related project anyhow.

Good luck on figuring this one out.

You misunderstood the ISP comment. I was not suggesting filtering by the ISP. I was suggesting that there be a way for the customer to monitor the logs of the sites visited for each individual internet account by an accountability partner. They keep records anyways of all the sites you visit for the police etc just like there are phone records of numbers called for phone accounts.

---

### Post by uncleclinto on 2008-11-13
[QUOTE=mssever;6141059]What happens if you run ```
sudo net-responsibility-report --debug
``` You can post the output if you like so I can take a look at it, but be sure to sanitize it, since it will contain sensitive information.



Okay, I did that.  Here's my output... "The debugger isn't installed. Exiting".

I've installed net responsibility.
I've installed postfix.
I've been looking for documentation... haven't found any.

What do I put on the line, "What is your mail server's name?"  I put smtp.comcast.net, but nothing happens.  I read something about postfix, but I'm not sure what that is.  I also read in an earlier post about setting smtp to "true" in the config file, but I can't even find it.  Where's that sucker at.  A little help here would be awesome.  I know shalamabobbi's questions are much more interesting, but it feels as though I'm being ignored.

anyone???  I'm not looking to improve the reports or make them cleaner... just having them sent would be nice.:confused:

---

### Post by mssever on 2008-11-13
> **uncleclinto said:**
> Okay, I did that.  Here's my output... "The debugger isn't installed. Exiting".What version of Net Responsibility are you using? The meaning of the --debug option changed at some point, and it appears that you're using an older version.

> What do I put on the line, "What is your mail server's name?"  I put smtp.comcast.net, but nothing happens.  I read something about postfix, but I'm not sure what that is.  I also read in an earlier post about setting smtp to "true" in the config file, but I can't even find it.
Postfix is an SMTP server you can use to send mail from your machine instead of using your ISP's SMTP server. Using it is quite advanced, and I'm not sufficiently knowledgeable to support it. Please define "nothing happens." Also, it might help to post your (sanitized) configuration file. But the debugging output from using a version that supports the current --debug switch will be definitive.
> Where's that sucker at.  A little help here would be awesome.  I know shalamabobbi's questions are much more interesting, but it feels as though I'm being ignored.
I apologize. I didn't deliberately ignore you. I simply overlooked your post.

---

### Post by uncleclinto on 2008-11-15
"Please define "nothing happens." Also, it might help to post your (sanitized) configuration file."

nothing happens = It's not sending emails to my accountability partners, which I thought was the point...

I said earlier, I can't find my config file.  Is it in "etc" somewhere?  Maybe "home"?

---

### Post by mssever on 2008-11-16
> **uncleclinto said:**
> "Please define "nothing happens." Also, it might help to post your (sanitized) configuration file."

nothing happens = It's not sending emails to my accountability partners, which I thought was the point...

I said earlier, I can't find my config file.  Is it in "etc" somewhere?  Maybe "home"?

Configuration files live in /etc. In this case, it's /etc/net-responsibility.conf. Note that it might contain sensitive information which you should sanitize.

Unless your configuration file contains an obvious error, it's not possible to help you further until you provide the other information I asked for. Unless something's obviously wrong with your configuration, the debugging info is the only way to find out what went wrong.

---

### Post by uncleclinto on 2008-11-17
--- %YAML:1.0
# This is the configuration file for Net Responsibility.
# It is in YAML format; the syntax should be quite obvious. If you need
# more details, see <http://yaml.org>.

# What is your name? At a minimum, Net Responsibility uses your name
# when sending reports. 
name: Clint

# What e-mail address should reports come from? Change this to your
# e-mail address.
email_from: [email]sanitized@comcast.net[/email]

# List here the e-mail address(es) to receive reports. For example:
# email_to:
#   - [email]email@somedomain.com[/email]
#   - [email]another@email.com[/email]
email_to:
  - gcarpenter@sanitized
  - delolle@sanitized
  - walterswebdesign@sanitized

# Configure the server to use for sending e-mail. The pre-sets are for
# Postfix. If you use some other e-mail, fill this section in with the
# details provided by your e-mail provider or ISP.
#
# Once you've configured this section, set use_smtp to true. 
smtp_server:
  use_smtp : true      # Set to true when configured
  server   : smtp.comcast.net # localhost if you're using postfix
  port     : 25        # Default port: 25
  
  # The options below aren't implemented yet
  authentication: false # Whether this server requires authentication. Possible values: true, false
  login_name    : username
  password      : your password
  encryption    : none # What kind of encryption does this server require? Options: tls, ssl, none

# The location of the logfile and pidfile must be specified, else Net
# Responsibility will refuse to start.
# WARNING: Don't change these unless you know what you're doing!
logfile: /var/log/net-responsibility.log
pidfile: /var/run/net-responsibility.pid

---

### Post by mssever on 2008-11-17
> **uncleclinto said:**
> 
  # The options below aren't implemented yet
  authentication: false # Whether this server requires authentication. Possible values: true, false
  login_name    : username
  password      : your password
  encryption    : none # What kind of encryption does this server require? Options: tls, ssl, none
It looks like you didn't provide your login information for your SMTP server. I assume that Comcast requires a username and password before you can connect to their SMTP server.

Also, you still haven't answered my question about what version you're running. This is the third time I've asked. It's frustrating trying to help you when you don't provide the information I need to diagnose your problem.

---

### Post by uncleclinto on 2008-11-18
I'm really sorry about the version info...  I missed that.  I didn't mean to frustrate you.  I have a one-year-old, and I get a little distracted sometimes.  

I have the version that is in the Feisty Fawn repos... According to Synaptic it's version 4.3.  I'm really really sorry about that.

The config screen thingy that pops up in my terminal when I select "configure net responsibility" didn't ask for my Comcast info anywhere so I didn't know where to put it.  

I'm sorry if I sound like a complete imbecil, but I'm not so good at all the funky "sudo gedit" voodoo that everyone here seems to be so awesome at.  I can follow what someone suggests very successfully most of the time, but if I have to figure it out on my own...

Thanks for your help.  I'm really sorry if I seem scattered and panicked at times.

---

### Post by uncleclinto on 2008-11-18
should I uninstall 4.3 and install 5?

---

### Post by mssever on 2008-11-19
I assume you mean that you have version 0.4.3, since there is no 4.3. The ability to use external SMTP servers was added in 0.5. So you need to upgrade, as it's not possible to do what you want in the version you're running. After upgrading, run the configuration program again, and you'll see some new options.

---

### Post by uncleclinto on 2008-11-20
awesome!!!  Thanks so much for dealing with my apparent cluelessness...

God Bless,
Clint

---

### Post by uncleclinto on 2008-11-21
Okay, so I thought I was good to go...

what does this mean??

net-responsibility-report[19981]: Generating report
net-responsibility-report[19981]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[19981]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[19981]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:153:in 'close'
net-responsibility-report[19981]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[19981]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[19981]: => from /usr/local/bin/net-responsibility-report:119
/usr/lib/ruby/1.8/sqlite3/errors.rb:94:in `check': database is locked (SQLite3::BusyException)

---

### Post by mssever on 2008-11-21
> **uncleclinto said:**
> Okay, so I thought I was good to go...

what does this mean??

net-responsibility-report[19981]: Generating report
net-responsibility-report[19981]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! [COLOR=Red]**Otherwise, you can safely ignore it**[/COLOR] (I hope).
net-responsibility-report[19981]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[19981]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:153:in 'close'
net-responsibility-report[19981]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[19981]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[19981]: => from /usr/local/bin/net-responsibility-report:119
/usr/lib/ruby/1.8/sqlite3/errors.rb:94:in `check': database is locked (SQLite3::BusyException)
In some cases, the database raises a BusyException. It shouldn't do so, because it isn't busy. Nevertheless, I've never been able to figure out how to make it behave properly. At any rate, as far as I can tell it's harmless, hence the explanation I highlighted above. I could silence it altogether, but it seems foolish to swallow errors without a trace.

---

### Post by xjcannonx on 2008-11-30
Ok, so first of all, thanks for creating this program. 
Also I'm a bit of a nOOb.
I am having some trouble getting it to work though. I am working with 8.10, 64 bit, and for some reason the .deb package wouldn't install so I took your advice to build from source. 

So i did everything in the netresponsibilitylist file, including adding all the required packages but i didn't know what to do to configure the net-responsibility-daemon? So i just left it alone. When I try to do a report I get this error:

/usr/lib/ruby/1.8/sqlite3/errors.rb:62:in `check': no such table: events (SQLite3::SQLException)
	from /usr/lib/ruby/1.8/sqlite3/statement.rb:39:in `initialize'
	from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in `new'
	from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in `prepare'
	from /usr/lib/ruby/1.8/sqlite3/database.rb:245:in `query'
	from /usr/share/net-responsibility/lib/modules/db.rb:172:in `get_dates'
	from /usr/share/net-responsibility/lib/report.rb:38:in `initialize'
	from /usr/local/bin/net-responsibility-report:82:in `new'
	from /usr/local/bin/net-responsibility-report:82:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119

[B]My .conf file looks like this:
[/B]
---
# This is the configuration file for Net Responsibility.
# It is in YAML format; the syntax should be quite obvious. If you need
# more details, see <http://yaml.org>.

# What is your name? At a minimum, Net Responsibility uses your name
# when sending reports. 
name: Joseph

# What e-mail address should reports come from? Change this to your
# e-mail address.
email_from: My Email

# List here the e-mail address(es) to receive reports. For example:
# email_to:
#   - [email]testemail@gmail.com[/email]
#   - [email]testemail@yahoo.com[/email]
email_to:

# Configure the server to use for sending e-mail. The pre-sets are for
# Postfix. If you use some other e-mail, fill this section in with the
# details provided by your e-mail provider or ISP.
#
# Once you've configured this section, set use_smtp to true. 
smtp_server:
  use_smtp      : true     # Set to true when configured
  server        : smtp.gmail.com # localhost if you're using postfix
  port          : 587        # Default port: 25
  authentication: true    # Whether this server requires authentication. Possible values: true, false
  use_tls       : true  # Do you have to use TLS encryption? Possible values: true, false
  login_name    : [email]myusername@gmail.com[/email]
  Password      : mypassword

# The location of the logfile and pidfile must be specified, else Net
# Responsibility will refuse to start.
# WARNING: Don't change these unless you know what you're doing!
logfile: /var/log/net-responsibility.log
pidfile: /var/run/net-responsibility.pid

Any help would be greatly appreciated, thanks

---

### Post by mssever on 2008-11-30
> **xjcannonx said:**
> Ok, so first of all, thanks for creating this program. 
Also I'm a bit of a nOOb.
I am having some trouble getting it to work though. I am working with 8.10, 64 bit, and for some reason the .deb package wouldn't install so I took your advice to build from source. 

So i did everything in the netresponsibilitylist file, including adding all the required packages but i didn't know what to do to configure the net-responsibility-daemon? So i just left it alone. When I try to do a report I get this error:

```
/usr/lib/ruby/1.8/sqlite3/errors.rb:62:in `check': no such table: events (SQLite3::SQLException)
    from /usr/lib/ruby/1.8/sqlite3/statement.rb:39:in `initialize'
    from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in `new'
    from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in `prepare'
    from /usr/lib/ruby/1.8/sqlite3/database.rb:245:in `query'
    from /usr/share/net-responsibility/lib/modules/db.rb:172:in `get_dates'
    from /usr/share/net-responsibility/lib/report.rb:38:in `initialize'
    from /usr/local/bin/net-responsibility-report:82:in `new'
    from /usr/local/bin/net-responsibility-report:82:in `initialize'
    from /usr/local/bin/net-responsibility-report:119:in `new'
    from /usr/local/bin/net-responsibility-report:119
```
Try running it with the --debug switch. Maybe that'll tell us something. Note that the output of the --debug switch will likely contain sensitive information from your configuration, so be sure to sanitize it before posting. Also, for readability's sake, please use [noparse]```

```[/noparse] tags to surround output that you paste here.

Another thing to try is to verify that the logfile, /var/log/net-responsibility.log exists. If it does, how big is it?

Finally, can you describe the steps you used to build from source and install? It's possible you've done something wrong, since I've never seen this error before.

---

### Post by xjcannonx on 2008-12-01
> **mssever said:**
> D'oh. Try this one.

I took the .deb from here and installed it to replace some other files, did the 'configure net responsibility' again and everything appears to be working!! Don't know what the problem was but it works, thanks!

---

### Post by adyoung on 2008-12-11
I installed version 0.4.3 almost a year ago and had it working.  I then installed 0.5.0 from an .rpm and even though my config is set up when try to send a test report I get this:

```

administrator@Austin-desktop:~$ sudo net-responsibility-report
/usr/local/bin/net-responsibility-report:31:in `require': no such file to load -- sqlite3 (LoadError)
	from /usr/local/bin/net-responsibility-report:31
administrator@Austin-desktop:~$ 


```

I'm pretty "green" as far as linux goes so I would greatly appreciate any help!!

---

### Post by mssever on 2008-12-11
> **adyoung said:**
> I installed version 0.4.3 almost a year ago and had it working.  I then installed 0.5.0 from an .rpm and even though my config is set up when try to send a test report I get this:

```

administrator@Austin-desktop:~$ sudo net-responsibility-report
/usr/local/bin/net-responsibility-report:31:in `require': no such file to load -- sqlite3 (LoadError)
    from /usr/local/bin/net-responsibility-report:31
administrator@Austin-desktop:~$ 


```I'm pretty "green" as far as linux goes so I would greatly appreciate any help!!Make sure you have the Ruby sqlite3 bindings installed. In Ubuntu, the package is called libsqlite3-ruby, but since you're apparently using some other distro, the package name might be different.

---

### Post by adyoung on 2008-12-12
Thanks for the quick response.  I installed those bindings and it fixed that problem.  I couldn't get this one to work with my email acount, so I signed up for a gmail account.  Now I get this:

```

administrator@Austin-desktop:~$ sudo net-responsibility-report
net-responsibility-report[7214]: Generating report
net-responsibility-report[7214]: Sending report
send: 'ehlo [127.0.1.1]\r\n'
reply: '250-mx.google.com at your service, [66.60.190.17]\r\n'
reply: '250-SIZE 35651584\r\n'
reply: '250-8BITMIME\r\n'
reply: '250-STARTTLS\r\n'
reply: '250 ENHANCEDSTATUSCODES\r\n'
reply: retcode (250); Msg: mx.google.com at your service, [66.60.190.17]
SIZE 35651584
8BITMIME
STARTTLS
ENHANCEDSTATUSCODES
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 87, in <module>
    s.login(smtpinfo['login_name'], smtpinfo['password'])
  File "/usr/lib/python2.5/smtplib.py", line 554, in login
    raise SMTPException("SMTP AUTH extension not supported by server.")
smtplib.SMTPException: SMTP AUTH extension not supported by server.
net-responsibility-report[7214]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[7214]: /usr/lib/ruby/1.8/sqlite3/errors.rb:94:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[7214]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:154:in 'close'
net-responsibility-report[7214]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[7214]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[7214]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/report_mailer.rb:83:in `send_message': send-report.py exited due to an unhandled exception. (RuntimeError)
	from /usr/share/net-responsibility/lib/report_mailer.rb:93:in `create_and_send'
	from /usr/local/bin/net-responsibility-report:89:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119
administrator@Austin-desktop:~$ 


```

When I configured it I put in smtp.google.com for the server name, used port 587, for the server authentification I said yes and used the user name and password from my gmail account. I also said no to TLS (it didn't work when I said yes). Any Ideas?

---

### Post by adyoung on 2008-12-12
Oh, and I am running Ubuntu 8.04 Hardy Heron

---

### Post by mssever on 2008-12-12
> **adyoung said:**
> When I configured it I put in smtp.google.com for the server name, used port 587, for the server authentification I said yes and used the user name and password from my gmail account. I also said no to TLS (it didn't work when I said yes). Any Ideas?
The correct settings for Gmail are:

[LIST]
[*]SMTP server: smtp.gmail.com
[*]Port: 587
[*]Use TLS authentication: yes
[/LIST]
These can be found if you go to Gmail's settings, and get help on configuring POP or IMAP access (for desktop e-mail clients). [http://mail.google.com/support/bin/answer.py?answer=13287](http://mail.google.com/support/bin/answer.py?answer=13287)
 > **adyoung said:**
> Oh, and I am running Ubuntu 8.04 Hardy Heron
In that case, you shouldn't be using the RPM. Ubuntu uses .deb packages.

---

### Post by CAPLinux on 2008-12-12
mssever, I have installed Net-Responsibility 0.5.0 on Ubuntu 8.10.  When I run net-responsibility-report, it does generate a report to my Gmail account.  My question is, when does it send the reports automaticly?  I checked /etc/cron.weekly and then /etc/cron.daily and found net-responsibility-report there, but I haven't received any reports that were sent automaticly yet.  What am I doing wrong here?

Thanks for your help! I love the idea of this application.

---

### Post by CAPLinux on 2008-12-12
mssever, Disregard my last post, as soon as I wrote it, I checked my email, and the report is there.  This report is extreamly large, it is picking up every URL that is on a web page.  This may be a bit much but, I know it is better then not having it.

Thanks again!!

---

### Post by bud1960 on 2008-12-13
Hi

I log user activity on my website and I notice that when I am using Covenant Eyes, I see the initial hit from Covenant Eyes followed by my hit.  Don't know if that is helpful at all or not, but it is my 2 cents worth.

Thanks,
Bud
[http://www.ehymns.org](http://www.ehymns.org)

---

### Post by mssever on 2008-12-14
Post deleted

---

### Post by adyoung on 2008-12-14
Thanks for all the help I finally got it working...  Now I would like to integrate the dan's guardian list into the emails so that it scores the URLs something like eric.duveau did in the post I attached.  However since I am using version 0.5.0 and not using postfix, I don't feel like I can exactly follow the instructions he has on here exactly as they are.  I don't have enough expertise to modify them myself, if someone knows how to do this, I would really appreciate the advice!!




> **eric.duveau said:**
> I have done something similar:

**1) configure postfix (used smarthost):**
sudo -s
dpkg-reconfigure postfix
test with:
mail -s testpostfix [email]youremail@yahoo.com[/email]
tail -f /var/log/mail.info
**2) monitoring process email dansguardian DENIED content**
sudo -s
crontab -l
*/1 *	* * * /usr/local/sbin/rtmon 

cat /usr/local/sbin/rtmon 
#!/bin/bash
cat /var/log/dansguardian/access.log | grep DENIED > /var/log/dansguardian/rt.log
longueur=`cat /var/log/dansguardian/rt.log | wc -l`
limite=5
if (("$longueur" >= "$limite")); then
  cat /var/log/dansguardian/rt.log | mail -s "Alert Monitoring for DUVEAU" [email]eric.duveau@9mail.com[/email]
cp /dev/null /var/log/dansguardian/access.log
fi

---

### Post by mssever on 2008-12-14
> **adyoung said:**
> Thanks for all the help I finally got it working...  Now I would like to integrate the dan's guardian list into the emails so that it scores the URLs something like eric.duveau did in the post I attached.  However since I am using version 0.5.0 and not using postfix, I don't feel like I can exactly follow the instructions he has on here exactly as they are.  I don't have enough expertise to modify them myself, if someone knows how to do this, I would really appreciate the advice!!
You should be able to follow what you quoted regardless of if/what version of Net Responsibility is installed. eric.duveau's tricks deal with dansguardian and don't affect Net Responsibility at all. Read the man pages for the various commands he gives if you don't understand them. Of particular note, read both man 1 crontab and man 5 crontab. Note that /usr/local/sbin/rtmon is a script that eric.duveau wrote (which he includes in his post).

Now, if you're wanting to actually alter the contents of the e-mails Net Responsibility sends (eric.duveau's code doesn't do that), you'll have to hack into Net Responsibility itself, which will require you to know Ruby.

---

### Post by toyonut on 2008-12-17
would it be possible to run a command like grep with a selection of keywords over the log file and write the results to another file which is then sent?
Just been thinking over this to try come up with an easy way to reduce the volume of information which is sent.
It may not give information in an orderly way like the current report does though.

---

### Post by mssever on 2008-12-17
> **toyonut said:**
> would it be possible to run a command like grep with a selection of keywords over the log file and write the results to another file which is then sent?
Just been thinking over this to try come up with an easy way to reduce the volume of information which is sent.
It may not give information in an orderly way like the current report does though.
grep won't work, because the logfile is an SQLite3 database. However, you could use some sort of SQL tool on it.

---

### Post by Bakerconspiracy on 2008-12-17
Doesn't the government do this already for us?

Just messing with you. Who is the target audience for this project? And how can this be viewed/ported to windows and mac? 

What ever happened to trust - Is that not good enough anymore? My intention is not to be insulting. Its just the idea of this project goes against many beliefs that I hold close. How could you monitor someone without feeling guilty?

I think this would work well for children at school - if there was a way to index the results and search through it really quickly (<- maybe graph theory? Who knows!) It automatically flags certain keywords?

---

### Post by mssever on 2008-12-17
> **Bakerconspiracy said:**
> Just messing with you. Who is the target audience for this project? And how can this be viewed/ported to windows and mac? 

What ever happened to trust - Is that not good enough anymore? My intention is not to be insulting. Its just the idea of this project goes against many beliefs that I hold close. How could you monitor someone without feeling guilty?

I think this would work well for children at school - if there was a way to index the results and search through it really quickly (<- maybe graph theory? Who knows!) It automatically flags certain keywords?
The target audience is people who want some accountability to help prevent them from doing something online that they believe that they shouldn't be doing. The two most popular examples are porn and gambling. This is different from a filter. Net Responsibility doesn't block any sites. Instead, it simply reports the sites you visit to your accountability partner(s). That way, of you visit sites you've agreed not to visit, the partner(s) can call you on it. This can be an effective way to help people to change their habits.

There's nothing sneaky about this, and no reason to feel guilty, because the accountable person installs the software with full knowledge of what it does, and chooses who gets the reports. All parties involved agree to monitoring. Nothing is forced. If you don't like that, you don't have to use it.

As far as porting goes, there is commercial accountability software for Windows that is much better than my program, and I think there is also Mac software available. I'm sure it would be possible to port Net Responsibility to another OS, but I'm not interested in doing so. It's open source, so if someone wants a port, they're welcome to port it. (Note that Net Responsibility hasn't been designed with portability in mind, and I make no apologies for that fact.)

---

### Post by jonathonblake on 2008-12-18
> **Bakerconspiracy said:**
> 
What ever happened to trust - Is that not good enough anymore? 


The target audience is an individual who trusts others, but isn't sure that they have enough whatever, to not do that which they do not want to do.  By installing this tool, those individuals get somebody who helps them, by calling them when they do that which they do not want to do. 

> Its just the idea of this project goes against many beliefs that I hold close. How could you monitor someone without feeling guilty?


Both the person being monitored, and the person who do the monitoring do so with full, informed consent, and knowledge.  

It can be hard for the person who does the monitoring. It does take a certain mindset to confront an individual with their actions, when those actions are those that the individual said they would not do/do not want to do.

> I think this would work well for children at school - if there was a way to index the results and search through it really quickly (<- maybe graph theory? Who knows!) It automatically flags certain keywords?

Whilst that is a potential use, it is not what this application is designed for.   Furthermore, tools like DansGuardian would be more appropriate, since they block the site, rather than display it.

jonathon

---

### Post by pinotmerlot on 2009-01-06
Hi there :

Well ive just installed this lovely program and have a few q s . When installing it how does it confirm to your accountability partner that they have been chosen .? I know of xxxchurch who is able to confirm . 

Regards 

Pinotmerlot

---

### Post by mssever on 2009-01-06
> **pinotmerlot said:**
> Hi there :

Well ive just installed this lovely program and have a few q s . When installing it how does it confirm to your accountability partner that they have been chosen .? I know of xxxchurch who is able to confirm . 

Regards 

Pinotmerlot
I'm not familiar with what X3 does, so I don't know how Net Responsibility compares. Net Responsibility sends reports to the accountability partner(s) on a regular basis. It's up to you to decide how to let them know that they'll be getting accountability reports.

---

### Post by pinotmerlot on 2009-01-08
thanks anyway i really am happy to use this program the other program is designed for windows so this program being designed for ubuntu works in a different way :P

regards
Pinotmerlot

---

### Post by JSuresh on 2009-01-09
This program looks awesome :KS

I was able to generate a report by typing ```
sudo net-responsibility-report
```

However, the report that it generated was a bit overwhelming.  Is there a more concise/readable output setting?

Thanks!

---

### Post by mssever on 2009-01-11
> **JSuresh said:**
>  Is there a more concise/readable output setting?
Not currently.

---

### Post by mugg326 on 2009-03-03
Hi guys.  Thank you very much for the time you have put into this project.  I am a relative noob, but I would like to install and help you test as necessary.  I am running Hardy on a Turion 64 dual core with 2Gb RAM.  I have tried installing the .deb package from sourceforge, but I keep getting the following error message:

    dpkg: error processing /home/adam/Desktop/netresponsibility-0.5.0.deb
    (--install):
     package architecture (i386) does not match system (amd64)
    Errors were encountered while processing:
     /home/adam/Desktop/netresponsibility-0.5.0.deb

How do I reconcile 32-bit software to 64-bit architecture?  Or am I missing something else?

---

### Post by Mickeyj4j on 2009-03-08
I'm using Linux mint 6 A Ubuntu based distro. i have installed net responsibility and when I click on the configure net responsibility nothing happens. I need to be able to set it up ion my system to protect all using it. Can any one out there help me. I can't find anything on how to do this in linux mint yet.

---

### Post by mssever on 2009-03-08
> **mugg326 said:**
> Hi guys.  Thank you very much for the time you have put into this project.  I am a relative noob, but I would like to install and help you test as necessary.  I am running Hardy on a Turion 64 dual core with 2Gb RAM.  I have tried installing the .deb package from sourceforge, but I keep getting the following error message:

    dpkg: error processing /home/adam/Desktop/netresponsibility-0.5.0.deb
    (--install):
     package architecture (i386) does not match system (amd64)
    Errors were encountered while processing:
     /home/adam/Desktop/netresponsibility-0.5.0.deb

How do I reconcile 32-bit software to 64-bit architecture?  Or am I missing something else?Use the most recent version of Net Responsibility, not an outdated one.
> **Mickeyj4j said:**
> I'm using Linux mint 6 A Ubuntu based distro. i have installed net responsibility and when I click on the configure net responsibility nothing happens. I need to be able to set it up ion my system to protect all using it. Can any one out there help me. I can't find anything on how to do this in linux mint yet.
Please post the output of running ```
sudo net-responsibility-config-cli
``` Sanitize it if appropriate.

---

### Post by Mickeyj4j on 2009-03-09
> **Mickeyj4j said:**
> I'm using Linux mint 6 A Ubuntu based distro. i have installed net responsibility and when I click on the configure net responsibility nothing happens. I need to be able to set it up ion my system to protect all using it. Can any one out there help me. I can't find anything on how to do this in Linux mint yet.

I found the solution to this. its strange but My friend said that when he set it up in Mint he somehow randomly thought to drag and drop the icon under the menu window onto the desktop and it worked fine.

---

### Post by mssever on 2009-03-10
> **Mickeyj4j said:**
> I found the solution to this. its strange but My friend said that when he set it up in Mint he somehow randomly thought to drag and drop the icon under the menu window onto the desktop and it worked fine.
That's weird. I have no idea why that worked, but I'm glad it did.

---

### Post by pinotmerlot on 2009-03-16
Hi there :

Im the friend of mickeyj4j and I had tried everything possible to get it working untill by prayer the idea came to me to drag and drop it !:popcorn:

Does anybody know why it works in ubuntu ?


Prayer does work 
amen 

Otherwise now that the program is installed how often does it send a report and how do you know its that particular program that sends a report?

regargs 
Pinotmerlot

---

### Post by mssever on 2009-03-17
> **pinotmerlot said:**
> Otherwise now that the program is installed how often does it send a report and how do you know its that particular program that sends a report?
The report is sent daily and contains "Net Responsibility" in the subject line.

---

### Post by roggan87 on 2009-03-23
Hi!
This is exactly what I've been looking for, thanks for you effort in making this software!

I'm currently using X3Watch on a Win-computer, but I'm planning to get my old laptop usable again. I've installed Puppy linux because it's the best alternative (it's a PIII 700Mhz with 128mb RAM)

I downloaded the source, but realized there was no ./configure file to compile normally, instead there was a ./configure-packages which made nothing but scripts to make a .deb file or a .rpm file. 

I've managed to install net responsibility through the rpm file, but it doesn't find sqlite3 or daemonize, even though these are installed.

I'm no expert on linux, but with a little help I hope I can manage this. Maybe it would be easier to compile the program to other distros with a regular ./configure file?

I really hope to get this working, or else I won't be able to use my laptop, and installing Ubuntu is not an alternative.

God bless!

---

### Post by mssever on 2009-03-24
> **roggan87 said:**
> I'm no expert on linux, but with a little help I hope I can manage this. Maybe it would be easier to compile the program to other distros with a regular ./configure file?

I really hope to get this working, or else I won't be able to use my laptop, and installing Ubuntu is not an alternative.
You're right that a more general approach to installation would be nice to have. The typical ```
./configure && make && sudo make install
``` approach isn't appropriate for this program, but using setup.rb (or setup.py) would be ideal. Patches are welcome.

As far as sqlite3 and daemonize go, make sure that you have the Ruby bindings for those libraries, and that they're installed in the standard locations.

---

### Post by roggan87 on 2009-03-27
Thanks for the quick answer.

> As far as sqlite3 and daemonize go, make sure that you have the Ruby bindings for those libraries, and that they're installed in the standard locations.

I've found the locations, but I'm not sure how to change the bindings... I tried to change the code a little to search in the right direction like this:

```
require '/usr/local/lib/ruby/gems/1.8/gems/daemons-1.0.10/lib/daemons/daemonize.rb'
```

This doesn't seem like the best solution, but it's working for net-responsibility-daemon. When I try to do the same with net-responsibility-report I get another error message. First the code:

```
require "/usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3.rb"
```

Then the output:
/usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3.rb:1:in `require' : no such file to load -- sqlite3/database (LoadError)
   from   /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3.rb:1
      from /usr/local/bin/net-responsibility-report:31:in `require' 
      from /usr/local/bin/net-responsibility-report:31

The file database.rb is in this directory: /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3/

I've also tried these paths:
```
require "/usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3"
```
```
require "/usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/"
```

I've heard something about the $LOAD_PATH that I think will fix this, but I don't really know how to configure it?

God bless!

---

### Post by mssever on 2009-03-28
> **roggan87 said:**
> Thanks for the quick answer.



I've found the locations, but I'm not sure how to change the bindings... I tried to change the code a little to search in the right direction like this:

```
require '/usr/local/lib/ruby/gems/1.8/gems/daemons-1.0.10/lib/daemons/daemonize.rb'
```This doesn't seem like the best solution, but it's working for net-responsibility-daemon. When I try to do the same with net-responsibility-report I get another error message. First the code:

```
require "/usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3.rb"
```Then the output:
/usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3.rb:1:in `require' : no such file to load -- sqlite3/database (LoadError)
   from   /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3.rb:1
      from /usr/local/bin/net-responsibility-report:31:in `require' 
      from /usr/local/bin/net-responsibility-report:31

The file database.rb is in this directory: /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3/

I've also tried these paths:
```
require "/usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3"
``````
require "/usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/"
```I've heard something about the $LOAD_PATH that I think will fix this, but I don't really know how to configure it?

God bless!
It appears that you installed sqlite3 and daemons as Ruby Gems, instead of using the packaged version. In that case, adding ```
require 'rubygems'
```before all the other require statements should do the trick.

You can also append directories to the library search path thus: ```
$:.push '/path/to/the/directory'
```However, I recommend you try requiring rubygems first, since that's the canonical way to do things. My code doesn't do that because I don't want to depend on rubygems; it's a lot simpler to depend on distro packages. However, I've never run Net Responsibility outside Ubuntu, so I'm not necessarily aware of the issues users of other distros face.

---

### Post by roggan87 on 2009-04-06
Thanks again, I've been trying to get this working now, and I've come a bit further.
It didn't work to require rubygems, so I added $:.push 'path' instead. Now I think net-responsibility-daemon is working, at least I don't get any error-message when I run it from the terminal. Is there a simple way to see if the program is running? Also I need to know if it starts at boot. 

When I try to run net-responsibility-report I get the following message:
```
/usr/local/.../sqlite/errors.rb:62_in 'check': no such table: events /SQLite3::SQLException)
    from ...
    from ...
    and so on...
```

I suspect that daemon haven't written anything to the database, and therefor there is nothing to load, is that correct? Or is it anything else that I'm missing?

Thanks in advance!
Robert

---

### Post by mssever on 2009-04-07
> **roggan87 said:**
> Thanks again, I've been trying to get this working now, and I've come a bit further.
It didn't work to require rubygems, so I added $:.push 'path' instead. Now I think net-responsibility-daemon is working, at least I don't get any error-message when I run it from the terminal. Is there a simple way to see if the program is running? Also I need to know if it starts at boot. 

When I try to run net-responsibility-report I get the following message:
```
/usr/local/.../sqlite/errors.rb:62_in 'check': no such table: events /SQLite3::SQLException)
    from ...
    from ...
    and so on...
```I suspect that daemon haven't written anything to the database, and therefor there is nothing to load, is that correct? Or is it anything else that I'm missing?

Thanks in advance!
Robert
Once a process daemonizes, it can no longer print output to the terminal. So to find any error messages that net-responsibility-daemon generates you have to look in the relevant logfile (/var/log/daemon.log). Alternatively, you can pass the --nodaemon option to net-responsibility-daemon to prevent it from daemonizing (mostly useful for testing). Try net-responsibility-daemon --help for a list of useful command line options.

The exception you printed suggests that the daemon never initialized the database for some reason. Since you didn't provide the full stack trace, I can't tell where the exception is coming from to verify my hypothesis. Error output from net-responsibility-daemon would be useful here.

To find out if a process (any process) is running, try ```
ps -ef | grep processname
```

The easiest way to find out if the daemon starts at boot is to reboot, then do a ps -ef as above (assuming that the daemon is already working correctly). Boot scripts are somewhat distro-dependant; the script I ship works with *buntu and (presumably) Debian. I don't know whether it works with Puppy. You might have to modify it by hand to get it to run.

---

### Post by roggan87 on 2009-04-07
Sorry about the incomplete terminal output. I cannot copy-paste from my terminal. However I've done some more effort in making it work. I looked in the logfile /var/log/messages and found out that I missed urlsnarf. Installed libnet and dsniff. I also installed a package that contained the pgrep-command. But I think I need some help from here. This is what I find in the logfile after running net-responsibility-daemon now:
```
Apr  7 16:54:47 (none) daemon.info net-responsibility-daemon[16523]: Starting
Apr  7 16:54:47 (none) daemon.info net-responsibility-daemon[16523]: Caught interrupt. Exiting.
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3/errors.rb:62:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: => from /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3/database.rb:121:in 'close'
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: => from /usr/share/net-responsibility/lib/logger.rb:111:in 'run'
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: => from /usr/local/bin/net-responsibility-daemon:121:in 'initialize'
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: => from /usr/local/bin/net-responsibility-daemon:118:in 'loop'
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: => from /usr/local/bin/net-responsibility-daemon:118:in 'initialize'
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: => from /usr/local/bin/net-responsibility-daemon:155:in 'new'
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: => from /usr/local/bin/net-responsibility-daemon:155
```

and 
```
ps -ef | grep net-responsibility-daemon
```
doesn't give any output. I use a mobile modem device (GPRS) to connect to internet, hope this works with net-responsibility-report.

One last thing. I get a file named /var/log/net-responsibility, but it contains nothing but 
```
SQLite format 3
```

---

### Post by mssever on 2009-04-07
> **roggan87 said:**
> Sorry about the incomplete terminal output. I cannot copy-paste from my terminal.If you're using gnome-terminal, <Ctrl><Shift>C copies and <Ctrl><Shift>V pastes. In classic xterm, selecting text automatically copies and middle-clicking pastes. If you use some other terminal, consult the documentation, because I'm quite sure there's a way to do it.

> This is what I find in the logfile after running net-responsibility-daemon now:
```
Apr  7 16:54:47 (none) daemon.debug net-responsibility-daemon[16523]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
```This is no concern.

> ```
ps -ef | grep net-responsibility-daemon
```doesn't give any output.Hmm... Try running with the --nodaemon option and see if it keeps running.> I use a mobile modem device (GPRS) to connect to internet, hope this works with net-responsibility-report.It shouldn't matter. But maybe urlsnarf (part of the dsniff package, at least in Ubuntu) is having trouble. Try running ```
urlsnarf -i any
``` as root and see if it picks up the websites you visit.

> One last thing. I get a file named /var/log/net-responsibility, but it contains nothing but 
```
SQLite format 3
```Either the file is corrupted or net-responsibility-daemon never initialized it for some reason. Try deleting that file and restarting the daemon--ideally with the --nodaemon option.

---

### Post by roggan87 on 2009-04-08
> If you're using gnome-terminal, <Ctrl><Shift>C copies and <Ctrl><Shift>V pastes. In classic xterm, selecting text automatically copies and middle-clicking pastes. If you use some other terminal, consult the documentation, because I'm quite sure there's a way to do it.
I was using rxvt, a terminal emulator, but now I've installed Sakura, another better one.

I've been doing some progress, but it's still not working completely. Urlsnarf is working. I tried with "urlsnarf -i any" But it didn't work, and I didn't know what to replace "any" with. But if I simply type "urlsnarf" then it works perfectly. 

Now I can get the report to run and send a message. This is the output in the terminal:

```
net-responsibility-report[21387]: Generating report
net-responsibility-report[21387]: Sending report
send: 'ehlo [127.0.0.1]\r\n'
reply: '250-mx.google.com at your service, [95.209.88.172]\r\n'
reply: '250-SIZE 35651584\r\n'
reply: '250-8BITMIME\r\n'
reply: '250-STARTTLS\r\n'
reply: '250-ENHANCEDSTATUSCODES\r\n'
reply: '250 PIPELINING\r\n'
reply: retcode (250); Msg: mx.google.com at your service, [95.209.88.172]
SIZE 35651584
8BITMIME
STARTTLS
ENHANCEDSTATUSCODES
PIPELINING
send: 'STARTTLS\r\n'
reply: '220 2.0.0 Ready to start TLS\r\n'
reply: retcode (220); Msg: 2.0.0 Ready to start TLS
send: 'ehlo [127.0.0.1]\r\n'
reply: '250-mx.google.com at your service, [95.209.88.172]\r\n'
reply: '250-SIZE 35651584\r\n'
reply: '250-8BITMIME\r\n'
reply: '250-AUTH LOGIN PLAIN\r\n'
reply: '250-ENHANCEDSTATUSCODES\r\n'
reply: '250 PIPELINING\r\n'
reply: retcode (250); Msg: mx.google.com at your service, [95.209.88.172]
SIZE 35651584
8BITMIME
AUTH LOGIN PLAIN
ENHANCEDSTATUSCODES
PIPELINING
send: 'AUTH PLAIN AHJvZ2dhbjg3QGdtYWlsLmNvbQBydXBlcnRzdGVpbg==\r\n'
reply: '235 2.7.0 Accepted\r\n'
reply: retcode (235); Msg: 2.7.0 Accepted
send: 'mail FROM:<robert_roger87@hotmail.com> size=947\r\n'
reply: '250 2.1.0 OK w5sm11814068mue.3\r\n'
reply: retcode (250); Msg: 2.1.0 OK w5sm11814068mue.3
send: 'rcpt TO:<robert_roger87@hotmail.com>\r\n'
reply: '250 2.1.5 OK w5sm11814068mue.3\r\n'
reply: retcode (250); Msg: 2.1.5 OK w5sm11814068mue.3
send: 'data\r\n'
reply: '354  Go ahead w5sm11814068mue.3\r\n'
reply: retcode (354); Msg: Go ahead w5sm11814068mue.3
data: (354, 'Go ahead w5sm11814068mue.3')
send: "From: RJ <robert_roger87@hotmail.com>\r\nTo: robert_roger87@hotmail.com\r\nSubject: RJ's Net Responsibility Report\r\nDate: Wed, 08 Apr 2009 11:00:35 +08:00\r\nMessage-Id: 155770.212377_21600000000.robert_roger87@hotmail.com\r\nContent-Type: text/plain\r\n\r\n####################\r\n## Startup Report ##\r\n####################\r\n\r\n    2009-04-08\r\n    ==========\r\n    \r\n        09:40:34: Start\r\n        10:48:39: Start\r\n        10:49:48: Start\r\n        10:49:58: Start\r\n        10:58:16: Start\r\n        10:58:44: Start\r\n    \r\n    \r\n#####################\r\n## Shutdown Report ##\r\n#####################\r\n\r\n    2009-04-08\r\n    ==========\r\n    \r\n        09:40:35: Interrupt\r\n        10:48:39: Interrupt\r\n        10:49:48: Interrupt\r\n        10:49:58: Interrupt\r\n        10:58:16: Interrupt\r\n        10:58:44: Interrupt\r\n    \r\n    \r\n################\r\n## URL Report ##\r\n################\r\n\r\n    2009-04-08\r\n    ==========\r\n    \r\n        Hostnames on this Day (Total: 0)\r\n        ================================\r\n.\r\n"
reply: '250 2.0.0 OK 1239181249 w5sm11814068mue.3\r\n'
reply: retcode (250); Msg: 2.0.0 OK 1239181249 w5sm11814068mue.3
data: (250, '2.0.0 OK 1239181249 w5sm11814068mue.3')
send: 'quit\r\n'
reply: '221 2.0.0 closing connection w5sm11814068mue.3\r\n'
reply: retcode (221); Msg: 2.0.0 closing connection w5sm11814068mue.3
net-responsibility-report[21387]: Rotating log
net-responsibility-report[21387]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[21387]: /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3/errors.rb:62:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[21387]: => from /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3/database.rb:121:in 'close'
net-responsibility-report[21387]: => from /usr/local/bin/net-responsibility-report:104:in 'initialize'
net-responsibility-report[21387]: => from /usr/local/bin/net-responsibility-report:120:in 'new' net-responsibility-report[21387]: => from /usr/local/bin/net-responsibility-report:120

```

I'm only worried about the last lines. However this is the mail that I get:

> ####################
## Startup Report ##
####################
 
    2009-04-08
    ==========
    
        09:40:34: Start
        10:48:39: Start
        10:49:48: Start
        10:49:58: Start
        10:58:16: Start
        10:58:44: Start
    
    
#####################
## Shutdown Report ##
#####################
 
    2009-04-08
    ==========
    
        09:40:35: Interrupt
        10:48:39: Interrupt
        10:49:48: Interrupt
        10:49:58: Interrupt
        10:58:16: Interrupt
        10:58:44: Interrupt
    
    
################
## URL Report ##
################
 
    2009-04-08
    ==========
    
        Hostnames on this Day (Total: 0)
        ================================

As you can see, the program saves start and interruption times, but it doesn't save visited website. (probably because the daemon is interupted before I even get to visit any website)

I tried to delete /var/log/net-responsibility.log but the new one looked exactly the same.

Here comes the complete output from daemon --nodaemon:

```
net-responsibility-daemon[24706]: Starting
net-responsibility-daemon[24706]: Caught interrupt. Exiting.
net-responsibility-daemon[24706]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-daemon[24706]: /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3/errors.rb:62:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-daemon[24706]: => from /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3/database.rb:121:in 'close'
net-responsibility-daemon[24706]: => from /usr/share/net-responsibility/lib/logger.rb:111:in 'run'
net-responsibility-daemon[24706]: => from /usr/local/bin/net-responsibility-daemon:121:in 'initialize'
net-responsibility-daemon[24706]: => from /usr/local/bin/net-responsibility-daemon:118:in 'loop'
net-responsibility-daemon[24706]: => from /usr/local/bin/net-responsibility-daemon:118:in 'initialize'
net-responsibility-daemon[24706]: => from /usr/local/bin/net-responsibility-daemon:155:in 'new'
net-responsibility-daemon[24706]: => from /usr/local/bin/net-responsibility-daemon:155

```

I only understand that something is wrong, but I don't really know the meaning of " Unable to close due to unfinalised statements" and why it says "Caught interrupt. Exiting."

Hope you have some clue to help me out, I think I'm close to get it working now!

---

### Post by mssever on 2009-04-08
> **roggan87 said:**
> I've been doing some progress, but it's still not working completely. Urlsnarf is working. I tried with "urlsnarf -i any" But it didn't work, and I didn't know what to replace "any" with. But if I simply type "urlsnarf" then it works perfectly.The -i argument is the interface to listen on. "any" means to listen on any interface, which is supposed to work in all cases. If you don't specify the interface, urlsnarf chooses a default. On my machine, the default is eth0, which is only correct if I'm connected to a wired network. Usually, though, I operate wirelessly, and my wireless card is wlan0.

The reason net-responsibility-daemon isn't recording any URLs is because it starts urlsnarf with -i any. Urlsnarf dies prematurely on your machine, which leads to the not-very-specific "interrupted" message. Probably urlsnarf isn't installed correctly on your machine. Otherwise, you should search the documentation and/or ask a urlsnarf expert to find out why urlsnarf-i any isn't working for you. 

> I tried to delete /var/log/net-responsibility.log but the new one looked exactly the same.Your report output demonstrates that net-responsibility.log contains more than you said it does. Otherwise, there's no way it could have output the interrupts and such. I don't think anything's wrong with the file.

> Here comes the complete output from daemon --nodaemon:

```
[B]net-responsibility-daemon[24706]: Starting
net-responsibility-daemon[24706]: Caught interrupt. Exiting.[/B]
[I]net-responsibility-daemon[24706]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-daemon[24706]: /usr/local/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.2.4/lib/sqlite3/errors.rb:62:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)[/I]
```I only understand that something is wrong, but I don't really know the meaning of " Unable to close due to unfinalised statements" and why it says "Caught interrupt. Exiting."I've snipped the uninteresting parts, but thanks for including the entire message. The part in bold is the startup note and the interrupt from urlsnarf dying prematurely. If you read the next line (in italics), you'll notice that it says that the following error is safe to ignore. It's a known issue, but I don't know what's causing it or how to fix it, and it doesn't appear to cause any problems.

---

### Post by roggan87 on 2009-04-08
> The -i argument is the interface to listen on. "any" means to listen on any interface, which is supposed to work in all cases. If you don't specify the interface, urlsnarf chooses a default. On my machine, the default is eth0, which is only correct if I'm connected to a wired network. Usually, though, I operate wirelessly, and my wireless card is wlan0.
Okay, now I understand why that's important. I've searched the net for some information on urlsnarf and interfaces, but found nothing of value. When i type "urlsnarf -i any" I get the following output:
```
# urlsnarf -i any
urlsnarf: ioctl: No such device
```
But then I tested -i all instead just to try, and it seems to work, have a look:
```
# urlsnarf -i all
Kernel filter, protocol ALL, datagram packet socket
urlsnarf: listening on all [tcp port 80 or port 8080 or port 3128]
95.209.40.230 - - [ 8/Apr/2009:17:39:38 +0800] "GET http://google.se/ HTTP/1.1" - - "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.7) Gecko/20071018 BonEcho/2.0.0.7"
95.209.40.230 - - [ 8/Apr/2009:17:39:39 +0800] "GET http://www.google.se/ HTTP/1.1" - - "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.7) Gecko/20071018 BonEcho/2.0.0.7"
95.209.40.230 - - [ 8/Apr/2009:17:39:39 +0800] "GET http://clients1.google.com/generate_204 HTTP/1.1" - - "http://www.google.se/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.7) Gecko/20071018 BonEcho/2.0.0.7"
95.209.40.230 - - [ 8/Apr/2009:17:39:40 +0800] "GET http://www.google.se/csi?v=3&s=webhp&action=&tran=undefined&ei=QMXcSdKzJpKQsAbbpKnlCQ&e=17259,20187,20233,20253&rt=prt.75,xjs.117,ol.645 HTTP/1.1" - - "http://www.google.se/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.7) Gecko/20071018 BonEcho/2.0.0.7"

```
Probably it's distro-dependent, how to handle interfaces. I'm no expert on Linux, but it's my best guess. I tried to edit the urlsnarf-command in logger.rb line 81, to 
```
urlsnarf = IO.popen("#{@urlsnarf} -i all 2> /dev/null")
```
 and now it seems to work perfectly! Daemon is logging the websites, and Report is mailing them. Please help me out if I'm wrong here, or if I've missed something.
 A thousand thanks for all your help, and may God bless you!

---

### Post by mssever on 2009-04-08
> **roggan87 said:**
> But then I tested -i all instead just to try, and it seems to work, have a look:
Thanks for that. Since "all" captures the intended meaning better, and since "all" works on my machine, I've adopted your discovery.

---

### Post by waspinator on 2009-04-24
I'd like to use this, but I've already upgraded to 9.04. Will this still work with it?

Oh and is a GUI ever being made for this? edit: never mind, just reread the first post. no time line though I'm guessing?

Also I'm not sure if I configured it wrong or not, but is there supposed to be an email sent to the person watching me right away and another to me saying that the configuration was a success? If not maybe that would be something to consider implement in a future? 

I used sudo net-responsibility-report and it did send a report to my watcher account but it was so incomprehensible that it's not all that useful. Perhaps my watcher needs to be a programmer. Is there a way to make it more ubuntu? (aka human)

Also, is there a way of setting the frequency of emails sent?

Thanks,

Waspinator

---

### Post by mssever on 2009-04-25
> **waspinator said:**
> I'd like to use this, but I've already upgraded to 9.04. Will this still work with it?Try it and see. I haven't upgraded yet (I plan to do so soon), so I don't know for sure, but I doubt anything will break.

> Oh and is a GUI ever being made for this? edit: never mind, just reread the first post. no time line though I'm guessing?These days, I have very little time for programming, so it's unlikely that I'll be making any changes to Net Responsibility any time soon. Maybe some other programmer will contribute some code.

> Also I'm not sure if I configured it wrong or not, but is there supposed to be an email sent to the person watching me right away and another to me saying that the configuration was a success? If not maybe that would be something to consider implement in a future?There's no confirmation message, though a way to send a test message would be useful. Patches are welcome.

> I used sudo net-responsibility-report and it did send a report to my watcher account but it was so incomprehensible that it's not all that useful. Perhaps my watcher needs to be a programmer. Is there a way to make it more ubuntu? (aka human)The e-mail currently contains just the raw data with minimal formatting. A suite of report analysis tools is needed (probably via a website), since e-mail isn't very good for this task. This has been on the to-do listfor quite a while, but I haven't had time to implement it. Again, contributions are welcome.

> Also, is there a way of setting the frequency of emails sent?
You can alter the symlinks in /etc/cron.*. Or, you can use root's crontab for more fine-grained control.

---

### Post by roggan87 on 2009-05-01
Hi there!

I've been doing some tweaking in the program, and I'd like to share my progress. I've never done any programming in ruby before, so I can not promise that the code is perfect, but it's working for me. These are the main differences:

+ net-responsibility-report connects to an online database and downloads one general blacklist with keywords, one individual blacklist and one individual whitelist with hostnames.

+ The responsibility mail does not show all starts and stops, but only date and time for interrupts. Then comes all matches agains the blacklists, then all hostnames and paths as usual. The mail comes in html-format, just a small improvement in design.

Since I know quite a bit of PHP and Mysql etc, the individual black/whitelists are not a big deal to do. As is right now it is only a general blacklist, but I plan to make a more user-friendly website where you can log in and add keywords to your personal blacklist and hostnames to your whitelist. These lists will be connected to your e-mail address which will serve as your username. It may also be useful to be able to delete entries in the lists, but maybe with e-mail notification to your responsibility person?

This is where I'm at, all comments are welcome! What do you think mssever, will this be implemented in some future version? Otherwise I guess I'll skip the user-friendly website...

Once again, thank you for your efforts in making this software, it's awesome!

---

### Post by mssever on 2009-05-04
> **roggan87 said:**
> Hi there!

I've been doing some tweaking in the program, and I'd like to share my progress. I've never done any programming in ruby before, so I can not promise that the code is perfect, but it's working for me. These are the main differences:

+ net-responsibility-report connects to an online database and downloads one general blacklist with keywords, one individual blacklist and one individual whitelist with hostnames.

+ The responsibility mail does not show all starts and stops, but only date and time for interrupts. Then comes all matches agains the blacklists, then all hostnames and paths as usual. The mail comes in html-format, just a small improvement in design.

Since I know quite a bit of PHP and Mysql etc, the individual black/whitelists are not a big deal to do. As is right now it is only a general blacklist, but I plan to make a more user-friendly website where you can log in and add keywords to your personal blacklist and hostnames to your whitelist. These lists will be connected to your e-mail address which will serve as your username. It may also be useful to be able to delete entries in the lists, but maybe with e-mail notification to your responsibility person?

This is where I'm at, all comments are welcome! What do you think mssever, will this be implemented in some future version? Otherwise I guess I'll skip the user-friendly website...

Once again, thank you for your efforts in making this software, it's awesome!
Sounds interesting. As far as keyword blacklisting goes, there might be some duplication with dansguardian.

I'd be interested to see the code.

---

### Post by roggan87 on 2009-05-05
Okay, I haven't heard of dansguardian before, maybe I'm doing this all in vain, but hey, it's a light and easy-to-use software and I simply like it!

Now I think I'm getting somewhere. I'll send the code, but I'm not really finished yet ;) This is what I've edited (also commented shortly in the code)

report.rb
url_report edited heavily
full_report slightly edited

options.rb
email_from option added (don't know if it will become useful)

report_mailer.rb
Content-type: text/html

db.rb
require "net/http"
get_warnings
get_stops
system_report - Now the daemon starts the report instead of cron. The reason is to work smoother with more distros, and to be able to change the frequency easier.

logger.rb
call system_report every 10th minute which may send a report

net-responsibility.conf
report_frequency: _days_between_reports - change manually, so far.

I think that's it for now. Hope to hear from you soon.

EDIT: Found a major bug, will come back when I've fixed this.

---

### Post by roggan87 on 2009-05-08
Please have a look at the code, I think it's working pretty much like I want it to. There are some small comments in the code, but feel free to ask me if there are any other questions. You can log in at deliterock.com/net-responsibility/ (Still very very simple) with email: test and password: test to edit the test blacklist. Right now it contains these words: test|two words|three small words|check|responsibility

Things I'm not really satisfied with:
-I get the database-lock error too often, (database is locked (SQLite3::BusyException)), this usually makes both report and daemon to stop. I don't have any obvious solution for this, and I don't know if there is any? Tried to change db.busy_timeout(), but without any luck. Right now the daemon starts the report to run separated, the best maybe would be to run report "inside" of daemon, so it doesn't lock the database... Maybe it would work if report could skip the daemon-restart if it was run with a flag like "net-responsibility-report --insidedaemon". It's hard to explain but I hope you get it.
-I'd like to categorize the warnings. I'd like to have several complete categories to choose from with one blacklist for each category. I think I can do this, if I just get some time.
-I've been thinking about if maybe the report should get the config-file from the server, and saving it on the disk every time before sending. This would make it almost impossible to change anything "like skipping the email_to addresses for one report" without email notification. Then you'd have to make all configurations online, and a mail with updates would be sent to your accountability-partners.
-One last thing. It would be nice to have like [www.net-responsibility.com|org|net](www.net-responsibility.com|org|net) if we get serious about this. I would be willing to pay a cheaper webhost, and I think it would be enough, but this lies on the future.

Think that's about it for now.

---

### Post by mssever on 2009-05-10
> **roggan87 said:**
> Things I'm not really satisfied with:
-I get the database-lock error too often, (database is locked (SQLite3::BusyException)), this usually makes both report and daemon to stop. I don't have any obvious solution for this, and I don't know if there is any? Tried to change db.busy_timeout(), but without any luck. Right now the daemon starts the report to run separated, the best maybe would be to run report "inside" of daemon, so it doesn't lock the database... Maybe it would work if report could skip the daemon-restart if it was run with a flag like "net-responsibility-report --insidedaemon". It's hard to explain but I hope you get it.
This error *is* annoying. If you ever figure out what's causing it, I'd be very grateful.

As far as the code goes, it's difficult to see what's changed without a diff. Would you be willing to post a unified diff?

---

### Post by roggan87 on 2009-05-10
Well, I'm not very familiar with diff-programs, but I've posted a unified diff now, hope you can use it. Or do you want me to explain in my own words what's changed? Or do you want me to make more explaining comments?

---

### Post by jbblack on 2009-05-12
Folks,

I'm really interested in this.  After I got everything working on my Ubuntu box (three days -_-), I discovered there really wasn't any accountability software for Linux - show stopper for me.  Sorry.  I really wanted to run Ubuntu, but I just cannot right now.  I cannot program and don't know how I could help.

---

### Post by roggan87 on 2009-05-13
> Folks,

I'm really interested in this. After I got everything working on my Ubuntu box (three days -_-), I discovered there really wasn't any accountability software for Linux - show stopper for me. Sorry. I really wanted to run Ubuntu, but I just cannot right now. I cannot program and don't know how I could help.

Jbblack, I know exactly what you mean! I'd just want to point out that Net Responsibility is working, and it IS an accountability software, but it's not really as functional as I'd like it to. I'm trying to make it more usable. My advice is to install it, and wait for the next release (and I hope it won't be too long).

God bless!

---

### Post by jbblack on 2009-05-13
> **roggan87 said:**
> Jbblack, I know exactly what you mean! I'd just want to point out that Net Responsibility is working, and it IS an accountability software, but it's not really as functional as I'd like it to. I'm trying to make it more usable. My advice is to install it, and wait for the next release (and I hope it won't be too long).

God bless!

Ok, I have re-installed Ubuntu and was looking for the file you previously posted in the forum.  I noticed you appear to have edited one of your posts.  I'm guessing that's the one that had the file link in it as you state the reason for edit is an update.  Looking forward as DansGuardian seems to be locking up my browser.

Thanks,
JB

---

### Post by roggan87 on 2009-05-14
Okay, here comes a new update...
Jbblack: Feel free to install this version, but at your own risk! It's still only tested by me, but it's working on my machine. Here's what you'll have to do:
- Install the real net-responsibility.deb package.
- Download the file posted here and extract into /usr/share/net-responsibility/
- Open /etc/net-responsiblity.conf and add the following lines:
```
#Here you can set the number of days between the reports if you don't use cron.
report_frequency: 1

#Here is the blacklist-categories that will be downloaded from the server.
blacklist_categories:
  - Porn
  - Pornstars
  - Models
  - Celebrities

```
You're absolutely free to change these values, especially the report_frequency.
- Delete /etc/cron.daily/net-responsibility-report
- Think that's all, please feel free to contact me if it doesn't work.

Well um, I hope I've solved the database-lock error by running report from inside the daemon which waits until the report is sent, and report doesn't restart daemon. Haven't tested fully, so it might be buggy, I don't know.
I've also added category-compatibility. Will add more categories later. Now you can choose which categories to block.
Report downloads the personal configuration file from the server (if there is any) before each mail. My plan is to have all configurations online. As you log out the changes will be saved, and a mail with the changes will be sent to the accountability partners.
I made the blacklist too complex, I'll change this next week. It takes too much time to send reports. Many of the keywords are not necessary.
I had to change the server (as you'll see) cause we canceled the other one, after three years of inactivity =)

---

### Post by jbblack on 2009-05-14
Roggan,

Sorry, you're going to have to forgive my ignorance.  I seem to only be generating errors, but I'm not well-versed enough to know if this is normal behavior or not.  This is copied from my terminal after running "sudo net-responsibility-report":

sudo net-responsibility-report
net-responsibility-report[32144]: Generating report
net-responsibility-report[32144]: Sending report
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 69, in <module>
    s = smtplib.SMTP(smtpinfo['server'], smtpinfo['port'])
  File "/usr/lib/python2.6/smtplib.py", line 241, in __init__
    raise SMTPConnectError(code, msg)
smtplib.SMTPConnectError: (-1, 'InterMail POP3 server ready.')
net-responsibility-report[32144]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[32144]: /usr/lib/ruby/1.8/sqlite3/errors.rb:62:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[32144]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:121:in 'close'
net-responsibility-report[32144]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[32144]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[32144]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/report_mailer.rb:83:in `send_message': send-report.py exited due to an unhandled exception. (RuntimeError)
	from /usr/share/net-responsibility/lib/report_mailer.rb:93:in `create_and_send'
	from /usr/local/bin/net-responsibility-report:89:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119

I took the new file, extracted it, and copied it to my /usr/share/net-responsibility directory.  I got no errors from the copy.

I edited the /etc/net-responsibility.conf file with the recommendations you provided.  I wasn't sure where to paste them, so I pasted them after "sending email" section.  Hmm...  I just noticed something - once I run configure, it deletes the added text from the .conf file.

Any idea what I'm doing wrong?

Thanks,
JB

---

### Post by roggan87 on 2009-05-16
JB,

I'm not really sure what's wrong, but I guess it's something with smtp, I think mssever knows this better. You're right about that config deletes the added lines, I haven't edited config yet. I'll try to get that to work as soon as possible. I the meantime, you'll have to run config, and add the lines afterwards (at the very end of the file). I wasn't clear on this, but try to do it in that order: config - add lines - report. This is my best guess right now.

Good luck!
Roggan

---

### Post by jbblack on 2009-05-17
Woohoo!!!

####################
## Startup Report ##
####################

   2009-05-17
   ==========

       15:55:18: Start


#####################
## Shutdown Report ##
#####################

   2009-05-17
   ==========



################
## URL Report ##
################

   2009-05-17
   ==========

       Hostnames on this Day (Total: 8 )
       ================================

       blizzard.vo.llnwd.net, en-us.[www.mozilla.com](www.mozilla.com), linux.about.com, suggestqueries.google.com,
       ubuntuforums.org, up.nytimes.com, [www.google.com](www.google.com), z.about.com... (truncated)

Roggan, thank you...  thank you...  thank you.

---

### Post by jbblack on 2009-05-17
Roggan,

On the shutdown time, will this log anytime I shut off the computer?  If so, it could look like I shut down the service.  I'll just leave my computer on for now.  Is there a way for it to record a shutdown in the service and one for the computer separately?

Hmm, is there a way for the emails to not display in the header as well?

Thanks again.

JB

---

### Post by roggan87 on 2009-05-18
JB, I'm glad you've got it working!

The report you posted is how the "old" report looks like, not like the one I've been working on. The files in /usr/share/net-responsibility/ where probably not replaced be the new ones. If you're comfortable with this, then never mind, just enjoy. If you'd like to try the new one, that also checks for "bad" keywords in the URLs, then you have to make sure you _replace_ the files with the newer ones. If you decide it's not worth the risk or the effort, then you have to _keep_ /etc/cron.daily/net-responsibility to send reports daily.

Well the mails will look like this:
```

####################
## Startup Report ##
####################
    
    2009-04-24
    ==========
    
        07:39:51: Start
        09:27:17: Start
        09:51:40: Start
        10:05:07: Start
        13:14:05: Start
        13:29:06: Start
    
#####################
## Shutdown Report ##
#####################
 
    2009-04-24
    ==========
    
        09:24:57: Signal
        09:50:56: Signal
        10:04:21: Signal
        10:20:59: Signal
        13:28:25: Signal
        15:20:07: Interrupt
 
```

Where Signal means the computer was shutdown properly, while Interrupt means the program was shutdown manually (Or by accident). I've changed this so it only shows the interrupts, but this depends if you choose to go with the "old" or the "new" edition...

I've edited the blacklists now, so there not huge.

And hey, I only do what I can, cause this is really important to me, but I'm glad if I can help in any way ;)
God bless, always!

---

### Post by jbblack on 2009-05-18
> **roggan87 said:**
> JB, I'm glad you've got it working!

The report you posted is how the "old" report looks like, not like the one I've been working on. The files in /usr/share/net-responsibility/ where probably not replaced be the new ones. If you're comfortable with this, then never mind, just enjoy. If you'd like to try the new one, that also checks for "bad" keywords in the URLs, then you have to make sure you _replace_ the files with the newer ones. If you decide it's not worth the risk or the effort, then you have to _keep_ /etc/cron.daily/net-responsibility to send reports daily.


Hmm...  need to get ready for work.  I'll try this when I get home.

Thanks,
JB

---

### Post by justinmiller87 on 2009-05-31
I must be missing it, but what file do I need to edit to determine how often this thing sends out an email? It would be kind of nice to know when I would expect it to be sending something out. Also, is there a way to cut out all the clutter and just send the first part of it where it just shows hostnames, not all the extra stuff?

Thanks,

Justin

---

### Post by Mickeyj4j on 2009-06-01
to all. i like this app. but it still has a long way to go. can you look into [www.xxxchurch.com](www.xxxchurch.com) and and see if you can incorperate there features into this app. i hate the fact that i have to tell the program to send the report and its not automatically done. 

I would love to help in the development of the app but got no experance and don't know how to.

---

### Post by kneewax on 2009-06-01
Hey Guys,

Just discovered this program and was going to install it and give it a go.  BUT the deb doesn't work on x64 installations - is there any chance of a 64-bit version?

cheers

---

### Post by MemphisJones on 2009-06-02
kneewax - try the .deb file from mssever at the top of page 19 on this thread.  That worked for my 64bit system.

---

### Post by kneewax on 2009-06-02
> **MemphisJones said:**
> kneewax - try the .deb file from mssever at the top of page 19 on this thread.  That worked for my 64bit system.

Aww, thats grand - worked a treat.  Thanks Memphis.

---

### Post by McMurdo on 2009-06-09
> **McManmanel said:**
> I was searching for Linux-based accountability software and I stumbled onto this thread.  I have a comment/question.

First background: I am running a dual-boot installation on my laptop with WinXP and Ubuntu.  I am trying to switch to Ubuntu but one of the things holding me back is that there is not accountability software for Ubuntu.  So I applaud you for your efforts.  Thank you!  I use Covenant Eyes on my XP installation.  

I think Afkpuz is right in part that Covenant Eyes (and X3?) use a comparison with a keyword list.  I'm sure they also have a blacklist database and some other checks and balances.  I know Covenant Eyes at least has a scoring system that gives numerical scores to each website based on the probability that it is inappropriate.  So there is quite a bit of functionality and complexity built into the whole system at least for Covenant Eyes.  Another thing they do is that the accountability partner can see at a glance whether there are websites in the weekly report that need some looking into because each report has an overall score at the top, thus saving the accountability partner from having to read through a long, and probably mostly meaningless, list of URLs.  And the weekly report is a highlights/summary of web usage with more detailed, site-by-site information available on the Covenant Eyes website.

I don't know much about programming and even less about Ubuntu/Linux, but my question is: have you thought about the possibility that there could just be a Linux front-end that runs in Ubuntu and takes care of the logging of URLs, etc. plus some other functions (security, making sure the user can't bypass the service, etc.)  But then maybe the URL log data could be passed to a program like Covenant Eyes to take advantage of their well-developed URL scoring algorithms and reporting systems?  If it is possible, the advantage of that approach is that it would save "reinventing the wheel" with regard to all the things Covenant Eyes already does well (scoring, blacklist DB, etc).  And it would necessitate only developing a Linux compatible front-end to collect and pass data.  (Of course it would also require that Covenant Eyes be willing to partner with your front end, but I am only green-lighting here.)  Another great advantage would likely be that you could get a working beta much sooner to help Ubuntu users with accountability issues if they are willing to subscribe to Covenant Eyes.  And if you still want to develop a totally independent GNU-public license package, the Covenant Eyes partnership could be seen as a temporary or interim solution.  I'd be interested to know what your thoughts are on this.

> **mssever said:**
> I don't know the technical details of how Covenant Eyes works. If CE logs websites locally, then sends them to a server somewhere, then making Net Responsibility work with CE wouldn't be too hard (provided the folks at CE are cooperative). From an open source standpoint, I think it would be great if Net Responsibility could work with several different service providers, possibly including both CE and X3.

If, however, CE works by setting the computer to contact a central proxy server, then supporting it would basically require a re-write. Arguably, a central proxy server is the best way to go, but it isn't something I could do unless I found a way to pay for it (it would require at least one dedicated server--probably several--and sufficient bandwidth to handle all my users' Internet traffic).

Suggestions are welcome. Hard facts and specific contributions are even more welcome.

Any progress/news about this? I already knew about Net Responsibility, but I've just lately been thinking about this on my own, submitting data to CE servers. It seems plausible to me; in fact we might be able to reverse engineer it ourselves, but it would be really awesome if CE could give us some technical data (format of data, what port to use, etc).

---

### Post by funkydan2 on 2009-06-09
Covenant Eyes almost definitely just receives a list of URLs which your computer has connected to, rather than using a proxy system. (My basis for this is that some URLs which I visit are 'quota free' on my ISP and are still quota free when using CE. If CE used a proxy system then I would be 'charged' for download linux isos etc.).

This means that it's possible to reverse engineer the CE protocol and have NetResponsibility send its reports to the CE server (as long as the user has a CE account). I don't know if the CE guys would happily make NetResponsibility an official front end. Even though they would make money out of it (from people buying CE accounts), they seem to want to make sure that it's near impossible to circumvent the logging software, and thus they may not be happy with a program like NetResponsibility until the same level of anti-circumvention can be assured as the Windows version does.

---

### Post by McMurdo on 2009-06-12
> **funkydan2 said:**
> Covenant Eyes almost definitely just receives a list of URLs which your computer has connected to, rather than using a proxy system. (My basis for this is that some URLs which I visit are 'quota free' on my ISP and are still quota free when using CE. If CE used a proxy system then I would be 'charged' for download linux isos etc.).

This means that it's possible to reverse engineer the CE protocol and have NetResponsibility send its reports to the CE server (as long as the user has a CE account). I don't know if the CE guys would happily make NetResponsibility an official front end. Even though they would make money out of it (from people buying CE accounts), they seem to want to make sure that it's near impossible to circumvent the logging software, and thus they may not be happy with a program like NetResponsibility until the same level of anti-circumvention can be assured as the Windows version does.

I totally see what you're saying. This is good news (at least somewhat). However, as long as you're paying for an account, I think maybe they wouldn't mind another program feeding data to your account. It is better than nothing. In fact, it seems like a good effort to me when a Linux LiveCD is an easy way to *circumvent* CE.

---

### Post by roggan87 on 2009-06-15
Hi all!
I haven't been working with this program for a while now, and I'm still waiting for mssever to double-check the source. Hopefully this will be done soon. There are still some things to do, but it's working pretty good with the blacklists etc.

I think it's a great idea to cooperate with Covenant Eyes, but I do not own an account, so it would be difficult for me to do that part.

> Also, is there a way to cut out all the clutter and just send the first part of it where it just shows hostnames, not all the extra stuff?

I just updated the report.rb so it is possible to decide what parts to send. Just download this file and replace /usr/share/net-responsibility/lib/report.rb AND add these lines to the end of /etc/net-responsibility.conf:

```
report_parts:
  - info
  - shutdowns
  - warnings
  - hostnames
  - paths
```

Feel free to delete the lines you'd like to.

> to all. i like this app. but it still has a long way to go. can you look into [www.xxxchurch.com](www.xxxchurch.com) and and see if you can incorperate there features into this app. i hate the fact that i have to tell the program to send the report and its not automatically done.

I've been doing some work on this, please read my post #282 [http://ubuntuforums.org/showpost.php?p=7280046&postcount=282]("http://ubuntuforums.org/showpost.php?p=7280046&postcount=282") and feel free to try it out. You shouldn't have to send the reports manually. Well, these latest changes are still not complete, but fully working for me =)

I'd like to continue the work with this, when I get some time.
God bless you all!

---

### Post by McMurdo on 2009-07-05
Hey all, wanted to point out some good discussion going on about this over at [this]("http://www.covenanteyes.com/blog/2009/06/10/covenant-eyes-for-linux/") Covenant Eyes blog post. This looks like it could turn into something good.

(I commented on the post, so I'll reveal that I'm Nathaniel so you can connect the viewpoints).

---

### Post by smillerc on 2009-07-15
Roggan,

> **roggan87 said:**
> Hi all!
I haven't been working with this program for a while now, and I'm still waiting for mssever to double-check the source. Hopefully this will be done soon. There are still some things to do, but it's working pretty good with the blacklists etc.

I think it's a great idea to cooperate with Covenant Eyes, but I do not own an account, so it would be difficult for me to do that part.



I just updated the report.rb so it is possible to decide what parts to send. Just download this file and replace /usr/share/net-responsibility/lib/report.rb AND add these lines to the end of /etc/net-responsibility.conf:

```
report_parts:
  - info
  - shutdowns
  - warnings
  - hostnames
  - paths
```

Feel free to delete the lines you'd like to.



I've been doing some work on this, please read my post #282 [http://ubuntuforums.org/showpost.php?p=7280046&postcount=282]("http://ubuntuforums.org/showpost.php?p=7280046&postcount=282") and feel free to try it out. You shouldn't have to send the reports manually. Well, these latest changes are still not complete, but fully working for me =)

I'd like to continue the work with this, when I get some time.
God bless you all!

I've tried your new report and edited net-responsibility files and I keep getting error below:

Any suggestions?



net-responsibility-report[12344]: Generating report                                                   
Downloading blacklist for Porn                                                                        
Downloading blacklist for Pornstars                                                                   
Downloading blacklist for Models                                                                      
Downloading blacklist for Celebrities                                                                 
Downloading blacklist for [email]smillerc@gmail.com[/email]                                                          
Looking for bad keywords in the URLs...                                                               
net-responsibility-report[12344]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).                                                                                                              
net-responsibility-report[12344]: /usr/lib/ruby/1.8/sqlite3/errors.rb:62:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)                                                                                                                                                 
net-responsibility-report[12344]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:121:in 'close'                                                        
net-responsibility-report[12344]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[12344]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[12344]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/modules/db.rb:239:in `initialize': unmatched ): /striptease)">/ (RegexpError)
        from /usr/share/net-responsibility/lib/modules/db.rb:239:in `new'
        from /usr/share/net-responsibility/lib/modules/db.rb:239:in `get_warnings'
        from /usr/share/net-responsibility/lib/modules/db.rb:238:in `upto'
        from /usr/share/net-responsibility/lib/modules/db.rb:238:in `get_warnings'
        from /usr/share/net-responsibility/lib/modules/db.rb:236:in `each'
        from /usr/share/net-responsibility/lib/modules/db.rb:236:in `get_warnings'
        from /usr/lib/ruby/1.8/net/protocol.rb:135:in `each_with_index'
        from /usr/share/net-responsibility/lib/modules/db.rb:235:in `each'
        from /usr/share/net-responsibility/lib/modules/db.rb:235:in `each_with_index'
        from /usr/share/net-responsibility/lib/modules/db.rb:235:in `get_warnings'
        from /usr/lib/ruby/1.8/sqlite3/resultset.rb:148:in `each'
        from /usr/share/net-responsibility/lib/modules/db.rb:231:in `get_warnings'
        from /usr/share/net-responsibility/lib/report.rb:51:in `warning_report'
        from /usr/share/net-responsibility/lib/report.rb:47:in `each'
        from /usr/share/net-responsibility/lib/report.rb:47:in `warning_report'
        from /usr/share/net-responsibility/lib/report.rb:119:in `full_report'
        from /usr/local/bin/net-responsibility-report:88:in `initialize'
        from /usr/local/bin/net-responsibility-report:119:in `new'
        from /usr/local/bin/net-responsibility-report:119

---

### Post by McMurdo on 2009-07-28
*Maybe* I should post this in a different board, but what do you all think about starting an open letter to Covenant Eyes asking them for technical data so we can submit logs to their servers? With a bunch of signatures?

What do you think? Good idea or not? :)

---

### Post by aflores on 2009-08-22
what if i want to install this on my laptop where i have root privileges.  is there any way of preventing me from disabling the url logging, or to notify my accountability partners if i remove them?  as far as i can tell, there is no way to prevent me from doing this.  if i want to remove an accountability partner, i can do so without them knowing, which defeats the purpose of this program.

---

### Post by Theophilosity on 2009-08-22
But c'mon, even if those features were available (shutdown notification, etc), you could find a way around them. That's why software like this is just a supplement to a recovery group. It's not gonna fix you. Only the grace of God can do that, and it just so happens that God chooses to provide the kind of grace you need through other people.

---

### Post by beattyml1 on 2009-08-27
I'm using 64-bit and the ldeb made using epm for the latest version does not install it says wrong architecture and displays the architecture that I have.

I got the the deb from msserver back on page 19 to install but from reading the thread it sounds like a lot of great features have been added since then so I would love to have the latest version.

So could someone help me get the latest version?

Also is there a way to set it up for multiple users because I am not the only one that uses the computer?

---

### Post by MemphisJones on 2009-08-28
> **beattyml1 said:**
> I'm using 64-bit and the ldeb made using epm for the latest version does not install it says wrong architecture and displays the architecture that I have.

I got the the deb from msserver back on page 19 to install but from reading the thread it sounds like a lot of great features have been added since then so I would love to have the latest version.

So could someone help me get the latest version?

Also is there a way to set it up for multiple users because I am not the only one that uses the computer?

beattyml1 - I don't think there has been an update from 0.5, so you should have the latest, greatest from that deb.

---

### Post by roggan87 on 2009-09-05
Hi!
I've been doing some progress with the program, but it hasn't been tested for bugs etc. It would also require a separate website, where you could make your own account and edit your configurations, blacklists, whitelist, etc, and when you do, it would send an email to your accountability partners. I haven't had time to make the website, and I don't know if it's worth it?

Is anybody willing to test the program for bugs etc?
Is anybody willing to help me create this website?
Is anybody willing to pay for a website, or donate some space (must include support for PHP and MySQL)?

> Maybe I should post this in a different board, but what do you all think about starting an open letter to Covenant Eyes asking them for technical data so we can submit logs to their servers? With a bunch of signatures?

What do you think? Good idea or not? 

Good idea! I'd be willing to do the programming. 

> what if i want to install this on my laptop where i have root privileges. is there any way of preventing me from disabling the url logging, or to notify my accountability partners if i remove them? as far as i can tell, there is no way to prevent me from doing this. if i want to remove an accountability partner, i can do so without them knowing, which defeats the purpose of this program.

I don't know about the url logging, but with this unreleased beta version, you can't remove an accountability partner, because every time you send a report, it downloads your online configuration file. And if you remove them online, they'll get an email about this.

> I'm using 64-bit and the ldeb made using epm for the latest version does not install it says wrong architecture and displays the architecture that I have.

I got the the deb from msserver back on page 19 to install but from reading the thread it sounds like a lot of great features have been added since then so I would love to have the latest version.

So could someone help me get the latest version?

Also is there a way to set it up for multiple users because I am not the only one that uses the computer? 

0.5.0 is the latest stable version. I'm not really sure if it's possible to set it up to run with different users...

Well, I'd love to hear from you.

---

### Post by McMurdo on 2009-09-13
Sorry people, I haven't been around for a while. Must catch up. :)

> **roggan87 said:**
> Hi!
I've been doing some progress with the program, but it hasn't been tested for bugs etc. It would also require a separate website, where you could make your own account and edit your configurations, blacklists, whitelist, etc, and when you do, it would send an email to your accountability partners. I haven't had time to make the website, and I don't know if it's worth it?

Is anybody willing to test the program for bugs etc?
Is anybody willing to help me create this website?
Is anybody willing to pay for a website, or donate some space (must include support for PHP and MySQL)?



Maybe we can find someone who would be willing to buy some hosting and then we could set things up so we could pay for a lot of it with donations (monthly donations from us users would be great -- I think at least at the beginning here it would be pretty easy to share the cost).


> 
Good idea! I'd be willing to do the programming. 


Sweet. That's great. I think I'm going to start a separate thread about this (might be a couple days before I get it up. Because, if you think about it, it's not accountability software that fixes your problem. It's God's grace, as someone mentioned earlier (I assume most of us on this thread are Christians, but for those who aren't, it's true. Even if you won't admit that, I think you'll realize accountability software is not the ulitmate solution). Accountability software might be part of "getting help" (Christians help each other overcome sin and be accountable) for you.

But you realize, smart people can get around accountability software (LiveCD, anyone?), and the internet isn't the only place to get porn. So it's not really just about the accountability software, and we really need to keep that in mind (and I think at least some of you already do).

> 
I don't know about the url logging, but with this unreleased beta version, you can't remove an accountability partner, because every time you send a report, it downloads your online configuration file. And if you remove them online, they'll get an email about this.


So would you need an online server running for this, then?

---

### Post by roggan87 on 2009-09-14
> Maybe we can find someone who would be willing to buy some hosting and then we could set things up so we could pay for a lot of it with donations (monthly donations from us users would be great -- I think at least at the beginning here it would be pretty easy to share the cost).

Yes, hopefully we can find people who'd be willing to donate small amounts of money... To rent a webhotel here in Sweden would cost approximately $55 USD/Year. That includes support for hosting, PHP, MySQL, and a domain (.net, .com, .org etc.) Any suggestions for a good domainname? [www.net-responsibility.com?](www.net-responsibility.com?) Not a lot of money, and I can pay for now.

> So would you need an online server running for this, then?

Depends on what you mean. The only two necessary components would be the program installed on your computer, and an account on the website that's in progress. The program co-operates with the website. Hope that answers your question.

---

### Post by A Future Pilot on 2009-09-14
I just found this, it looks great!! I might could help build the website, but I don't know a _whole_ lot. :-) Here's a homeschool group website I built for my mom, just basic XHTML, and maybe a little CSS or JavaScript: [http://www.obliqueducators.com/](http://www.obliqueducators.com/)

I don't know what all the website would need, like I said, I just know basic stuff :)

I'm willing to learn whatever I don't know though, so if you can't find anyone who already knows everything needed, I'll help.

I also *might* be able to help with hosting, have to ask my mom (She's the one that "officially" owns the hosting account, it's her homeschool group :) ) And I can definitely help with testing, assuming that just means running the program, and trying out everything a user might want to do.

Tell me what you think.

John

---

### Post by A Future Pilot on 2009-09-14
Forgot to mention, I actually use Arch Linux, not Ubuntu, so I might could make a package for the Arch User Repository, if that'd be fine with you.

---

### Post by roggan87 on 2009-09-14
Hi John!

I'm very glad to hear that you're interested! I really appreciate your offer to help, and if you want to try the software to find bugs etc, that would be great. I really like that you're using Arch linux, and I think it's great if you want to make an Arch package of it. But please don't distribute it yet ;)

I've started to build the website already, and I think I'll have the acquired time. Thanks for the offer, but I'll keep in touch if I need more help on that area.

Robert

---

### Post by A Future Pilot on 2009-09-14
Hey, while looking around for accountability software, I found this too: [http://www.accountabilitypal.org/](http://www.accountabilitypal.org/)

I haven't tried it yet, but it looks like what you want Net Responsibility to be. Just wanted to show you! :-)

John

---

### Post by McMurdo on 2009-09-15
> **A Future Pilot said:**
> Hey, while looking around for accountability software, I found this too: [http://www.accountabilitypal.org/](http://www.accountabilitypal.org/)

I haven't tried it yet, but it looks like what you want Net Responsibility to be. Just wanted to show you! :-)

John

I'm thinking that's pretty well known around here (I've heard of it), but thanks anyway. Also, it hasn't been updated since 2004, so... humm.

---

### Post by Taelith Luthiel on 2009-09-18
[quote=roggan87;7946607]Yes, hopefully we can find people who'd be willing to donate small amounts of money... To rent a webhotel here in Sweden would cost approximately $55 USD/Year. That includes support for hosting, PHP, MySQL, and a domain (.net, .com, .org etc.) Any suggestions for a good domainname? [www.net-responsibility.com?]("http://www.net-responsibility.com?") Not a lot of money, and I can pay for now.
 
 
I am currently a Windows user and always have been but I really want to switch Linux and have settled on Puppy as my distribution of choice. I have never used any accountability software but I need to.
 
My questions are these:
- Can I install Net Responsbility on a Puppy machine?
- How long do you think it will take to become a functional software?
- I am not a programmer so can I help your work by beginning to pay my
membership fee now(for the rental of web space)
 
I have some understanding of how software and hardware work but aside from four years on MS Quick Basic, no programming experience. I also only have about ten hours' experience between Puppy and DSL. In other words, I would absolutely love to use Net Responsability but I may need someone to hold my hand for a while - if you know what I mean.
 
Any advice is appreciated. :)

---

### Post by McMurdo on 2009-09-20
> **Taelith Luthiel said:**
> [quote=roggan87;7946607]Yes, hopefully we can find people who'd be willing to donate small amounts of money... To rent a webhotel here in Sweden would cost approximately $55 USD/Year. That includes support for hosting, PHP, MySQL, and a domain (.net, .com, .org etc.) Any suggestions for a good domainname? [www.net-responsibility.com?]("http://www.net-responsibility.com?") Not a lot of money, and I can pay for now.
 
 
I am currently a Windows user and always have been but I really want to switch Linux and have settled on Puppy as my distribution of choice. I have never used any accountability software but I need to.
 
My questions are these:
- Can I install Net Responsbility on a Puppy machine?
- How long do you think it will take to become a functional software?
- I am not a programmer so can I help your work by beginning to pay my
membership fee now(for the rental of web space)
 
I have some understanding of how software and hardware work but aside from four years on MS Quick Basic, no programming experience. I also only have about ten hours' experience between Puppy and DSL. In other words, I would absolutely love to use Net Responsability but I may need someone to hold my hand for a while - if you know what I mean.
 
Any advice is appreciated. :)

Hmm, yeah, that sounds fairly cheap, about $4.5 a month. Of course, I hope it's decent hosting. We could run into issues if we put a huge load on the site and it's terrible shared hosting.

Re getting started with Net Responsibility -- I'm sure people will try to help you out as they can... and you already sound like you're knowledgeable and willing enough, what with knowing what PHP and MySQL are and toying with Puppy and DSL (not exactly what I'd call beginner distros).

**Ahem!!!**

Now for my plug. :biggrin::biggrin::biggrin:

So, I went ahead and started a thread about that letter to Covenant Eyes I was talking about. [Here it is]("http://ubuntuforums.org/showthread.php?t=1267544").

---

### Post by roggan87 on 2009-09-21
> **Taelith Luthiel said:**
>  
I am currently a Windows user and always have been but I really want to switch Linux and have settled on Puppy as my distribution of choice. I have never used any accountability software but I need to.
 
My questions are these:
- Can I install Net Responsbility on a Puppy machine?
- How long do you think it will take to become a functional software?
- I am not a programmer so can I help your work by beginning to pay my
membership fee now(for the rental of web space)
 
I have some understanding of how software and hardware work but aside from four years on MS Quick Basic, no programming experience. I also only have about ten hours' experience between Puppy and DSL. In other words, I would absolutely love to use Net Responsability but I may need someone to hold my hand for a while - if you know what I mean.
 
Any advice is appreciated. :)

Hi!
If you want a distro that's small and fast, yet very functional, Puppy Linux is the perfect choice (in my opinion). It also has a great user community that's very helpful. I can recommend it as long as you're willing to learn. BUT, if you want a distro that looks and feels more "like Windoze" I would recommend something else. Well, having that said, I've installed Net Responsibility on Puppy Linux, and it's also what I'm using while developing the software. So it can absolutely be done, and I will do my best to help you with that. The best would be if I could make a PET package of the program when it's a stable version.

Oh, when it comes to time estimation, I'm always to optimistic, but the program is ready for beta testing, and I need a webhotel, but as soon as I get hold of a webhotel, you can start testing it for bugs, while I make the real website.

Of course you can help us with the rental for the webhotel! I'm not really sure how to handle the donation process, but we'll figure it out.

> Hmm, yeah, that sounds fairly cheap, about $4.5 a month. Of course, I hope it's decent hosting. We could run into issues if we put a huge load on the site and it's terrible shared hosting.

Re getting started with Net Responsibility -- I'm sure people will try to help you out as they can... and you already sound like you're knowledgeable and willing enough, what with knowing what PHP and MySQL are and toying with Puppy and DSL (not exactly what I'd call beginner distros).

Ahem!!!

Now for my plug.

So, I went ahead and started a thread about that letter to Covenant Eyes I was talking about. Here it is. 

McMurdo!
I'm not sure if you replied to me or Taelith, but does it matter? :)

It's decent hosting. I've hosted some other sites there, and I haven't had problems. The thing with the website is, that it won't be that much traffic, for the logs, the reports will never be uploaded to this server. The only thing that will be uploaded and downloaded is the configuration files, and the blacklists/whitelists. However, if we find that we need a more expensive host, we can work that out later.

Nice work! I'll reply to that thread also.

I'm doing progress with the website, but I'd need to order the webhotel soon. What about [www.net-responsibility.com?](www.net-responsibility.com?) I'll take no comments as a "Yes".

Over and out.

---

### Post by McMurdo on 2009-09-22
> **roggan87 said:**
> 

McMurdo!
I'm not sure if you replied to me or Taelith, but does it matter? :)

It's decent hosting. I've hosted some other sites there, and I haven't had problems. The thing with the website is, that it won't be that much traffic, for the logs, the reports will never be uploaded to this server. The only thing that will be uploaded and downloaded is the configuration files, and the blacklists/whitelists. However, if we find that we need a more expensive host, we can work that out later.

Nice work! I'll reply to that thread also.

I'm doing progress with the website, but I'd need to order the webhotel soon. What about [www.net-responsibility.com?](www.net-responsibility.com?) I'll take no comments as a "Yes".

Over and out.

OK, I see about the traffic situ. Re the domain name -- why the dash and not just netresponsibility.com? It's available.

---

### Post by roggan87 on 2009-09-22
> Re the domain name -- why the dash and not just netresponsibility.com? It's available. 

Hmm yeah. I don't really know. I just thought that it's called net-responsibility in most places. Like /usr/share/net-responsibility and net-responsibility-daemon and net-responsiblity-report etc. But you've got a point there. Well, worth a thought.

---

### Post by McMurdo on 2009-09-22
> **roggan87 said:**
> Hmm yeah. I don't really know. I just thought that it's called net-responsibility in most places. Like /usr/share/net-responsibility and net-responsibility-daemon and net-responsiblity-report etc. But you've got a point there. Well, worth a thought.

Hmmm, you're right. Also, I'd add that most websites **don't** use dashes in the domain name. And I bet most people wouldn't think of typing in a dash by default (although I'm sure they could get there if that's the name of the website -- I'm just saying they probably don't think it's usual either).

---

### Post by roggan87 on 2009-09-23
> Hmmm, you're right. Also, I'd add that most websites don't use dashes in the domain name. And I bet most people wouldn't think of typing in a dash by default (although I'm sure they could get there if that's the name of the website -- I'm just saying they probably don't think it's usual either). 

Okay I agree, let's go for netresponsibility.com ;)

---

### Post by Taelith Luthiel on 2009-09-24
Roggan87, Thank you for clearing that confusion up with with my post. I can't figure out how to correctly quote a previous post.
 
Anyway, re the money - I will look into options for international bank transfer.  you're in Sweden, right?

---

### Post by roggan87 on 2009-09-25
You're welcome ;) If you want to quote something, you simply copy the text, paste it in the reply box, select it, and press the speech bubble above.

Yes I'm in Sweden, and thanks, I appreciate that.

---

### Post by tetralectic on 2009-09-25
> [roggan87]("http://ubuntuforums.org/member.php?u=796965") ... Of course you can help us with the rental for the webhotel! I'm not really sure how to handle the donation process, but we'll figure it out. ...> [Taelith Luthiel]("http://ubuntuforums.org/member.php?u=914712"): ... Anyway, re the money - I will look into options for international bank transfer.  you're in Sweden, right?> [roggan87]("http://ubuntuforums.org/member.php?u=796965"): ... Yes I'm in Sweden, and thanks, I appreciate that.Roggan87, I too would like to donate some money to this worthy project. I was thinking about using Xoom since it's cheap and relatively convenient:

[https://www.xoom.com/sendmoneynow/home](https://www.xoom.com/sendmoneynow/home)

What do you think?

---

### Post by roggan87 on 2009-09-27
> Roggan87, I too would like to donate some money to this worthy project. I was thinking about using Xoom since it's cheap and relatively convenient:

[https://www.xoom.com/sendmoneynow/home](https://www.xoom.com/sendmoneynow/home)

What do you think?

You guys are awesome! Looks good, but it depends on how big amounts of money we are talking about here. There's no panic about the money, I'll contact you when it's time...

---

### Post by Taelith Luthiel on 2009-09-28
Many thanks for the advice, roggan87.
 
> tetralectic: I too would like to donate some money to this worthy project. I was thinking about using Xoom since it's cheap and relatively convenient ... What do you think?
 
This would be good if just the two of us are footing the bill (there is a minimum of $25 per transaction) but I think it is not the long term solution unless people want to pay annually or less often for their subscription.  Also, I am not sure if I will be able to use it as I live in the UK.
 
I know of a way that will work from any country to any country without a transfer charge but it is a little technical, requiring international banking codes. This is also not a long-term solution, I think.

---

### Post by tetralectic on 2009-09-29
> [Roggan87]("http://ubuntuforums.org/member.php?u=796965"): There's no panic about the money, I'll contact you when it's time...Thanks :)

Re: Xoom
> [Roggan87]("http://ubuntuforums.org/member.php?u=796965"): Looks good, but it depends on how big amounts of money we are talking about here> [Taelith Luthiel]("http://ubuntuforums.org/member.php?u=914712"): This would be good if just the two of us are footing the bill (there is a minimum of $25 per transaction) but I think it is not the long term solution unless people want to pay annually or less often for their subscription.Good Point.

 > [Taelith Luthiel]("http://ubuntuforums.org/member.php?u=914712"): Also, I am not sure if I will be able to use it as I live in the UK.You can use Xoom from many countries including the UK


Perhaps this is a more viable option: PayPay

[https://www.paypay.com/](https://www.paypay.com/)
[https://www.paypay.com/b_menu/user_fees.php](https://www.paypay.com/b_menu/user_fees.php)

Just a thought

---

### Post by roggan87 on 2009-10-09
Hi all!

I've ordered the domain [www.netresponsibility.com](www.netresponsibility.com) now, and been working a little on the layout for the site, and I'm very excited about this. Please remember that this will take a while.

> Perhaps this is a more viable option: PayPay

[https://www.paypay.com/](https://www.paypay.com/)
[https://www.paypay.com/b_menu/user_fees.php](https://www.paypay.com/b_menu/user_fees.php)

Seems like it could be a better solution, but it wasn't very clear on international transfers.

I've got one question for you all: Is there anything positive about having the reports sent from your personal email address, or would it be as good with [email]report@netresponsibility.com[/email] for example? I think it would be easier for the users and me and everybody else to solve it like that. For example x3watch does it that way.

Please tell me your opinion!

---

### Post by tetralectic on 2009-10-10
> [roggan87]("http://ubuntuforums.org/member.php?u=796965"): I've ordered the domain [www.netresponsibility.com]("http://www.netresponsibility.com/") now, and been working a little on the layout for the site, and I'm very excited about this.That is wonderful news, and thank you :P

> [roggan87]("http://ubuntuforums.org/member.php?u=796965"): I've got one question for you all: Is there anything positive about having the reports sent from your personal email address, or would it be as good with [EMAIL="report@netresponsibility.com"]report@netresponsibility.com[/EMAIL] for example? I think it would be easier for the users and me and everybody else to solve it like that. For example x3watch does it that way.

Please tell me your opinion!I would prefer [EMAIL="report@netresponsibility.com"]report@netresponsibility.com[/EMAIL]. I have used x3watch on both Windows and Mac machines and like the fact that it helps keep my accountability relationship private since it's not obvious to anyone else who the report is from.

I know this belongs in another thread, if an approach to Covenant Eyes regarding submiting Net Responsibility logs to their excellent analysis software is rebuffed, I suspect we'll have more luck approaching x3watch since it's part of a church ministry with a focus on the harms cyber sex.

---

### Post by artoo36 on 2009-10-16
Hey, all. I am posting here because I can't find any official site for Net Responsibility at the moment... I am running 64-bit 9.04, but the .deb is the wrong architecture (32-bit). Someone much earlier in this thread suggested the link at the top of page 19, but that link comes with the following error message:

/tmp/netresponsibility-svn.20080703023549-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences

Does anyone have any suggestions? I would like to have something on my computer so that I can relax a bit, and I would prefer not to have to reinstall the 32-bit version.

By the by, if it helps any, I am using the package manager to open the file. Would something else do it?

Thanks!

---

### Post by artoo36 on 2009-10-16
Never mind. I fiddled and it worked.

---

### Post by CHBlackElk on 2009-10-17
I'm pretty sure I missed something. To tell the truth I'm new to linux and still very anxious to learn everything I can. So far this thread has answered everything for me except how to set it up to send from gmail. Like I said I may have missed something, I am a newbie, but I keep trying to send reports to test it and I the same error that's listed on the first page, and no email ever shows up. Is this my bad, or a bug?

---

### Post by semijoyful on 2009-10-24
I feel your pain.  I too have some difficulty getting this thing to send through the mail.  Of course I think it's just more n00b luck than anything else for me.  Here's my output when I generate report:

```

net-responsibility-report[6026]: Generating report
net-responsibility-report[6026]: Sending report
net-responsibility-report[6026]: SMTP is disabled. Sending report to standard out.
####################
## Startup Report ##
####################

    2009-10-24
    ==========
    
        09:03:16: Start
    
    
#####################
## Shutdown Report ##
#####################

    2009-10-24
    ==========
    
    
    
################
## URL Report ##
################

    2009-10-24
    ==========
    
        Hostnames on this Day (Total: 1)
        ================================
    
        mail.google.com
    
    
        mail.google.com
            Time: 09:03:59
            Path: /mail/channel/bind?VER=6&it=3600028&at=xn3j2w52rkvax3hkco4uy5n1eefx58&SID=7F29E9810E068BDB&RID=76409&zx=8crl86-xhphoc&t=1
    
    
net-responsibility-report[6026]: Rotating log
net-responsibility-report[6026]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[6026]: /usr/lib/ruby/1.8/sqlite3/errors.rb:62:in 'check': unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[6026]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:121:in 'close'
net-responsibility-report[6026]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[6026]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[6026]: => from /usr/local/bin/net-responsibility-report:119

```

Could someone help me get this to mail out?
Thanks!

Kirk

---

### Post by cesko1903 on 2009-10-26
Hello All,

Apologies for intruding into the technical discussions but I'm completely new to Ubuntu and I'm looking to install this program. 

I haven't been able to get the program to work so far and I will have to bite the bullet and return to Windows (in order to use CE) if I can't get it to work. Is there any document/webpage which contains step by step instructions for installing and configuring the program?

Many thanks in advance.

---

### Post by semijoyful on 2009-10-26
> **cesko1903 said:**
> Hello All,

Apologies for intruding into the technical discussions but I'm completely new to Ubuntu and I'm looking to install this program. 

I haven't been able to get the program to work so far and I will have to bite the bullet and return to Windows (in order to use CE) if I can't get it to work. Is there any document/webpage which contains step by step instructions for installing and configuring the program?

Many thanks in advance.
What version of Ubuntu and what architecture are you using (i.e. x86, AMD64).  If you're having a hard time with the compiling from source (like ahem myself) then use the .deb file, found at the project's webpage (see first post) or the top of page 19 of this thread for 64 bit architecture .deb.  Before you do so, make sure you have all the dependencies installed.  download the source file.  Untar it, and read the readme for a list of the dependencies.  sudo apt-install all the dependencies and then try the .deb package the is appropriate for you.  If you're using any new enough version of Ubuntu, you should be able to install the .deb with a few clicks of the old mouse.  Let me know.
Fellow CE user,

Kirk

---

### Post by semijoyful on 2009-10-26
Never mind on the configuring. I didn't originally see the Configure Net Responsibility tool. Now, here's a few questions for you:  What does the following mean?
```

~$ sudo net-responsibility-report
net-responsibility-report[8362]: Generating report
net-responsibility-report[8362]: Sending report
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 78, in <module>
    except (smtplib.SMTPException,smtplib.socket.error,socket.error), e:
NameError: name 'socket' is not defined
net-responsibility-report[8362]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[8362]: /usr/lib/ruby/1.8/sqlite3/errors.rb:62:in 'check': unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[8362]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:121:in 'close'
net-responsibility-report[8362]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[8362]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[8362]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/report_mailer.rb:86:in `send_message': send-report.py exited due to an unhandled exception. (RuntimeError)
	from /usr/share/net-responsibility/lib/report_mailer.rb:96:in `create_and_send'
	from /usr/local/bin/net-responsibility-report:89:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119

```
And,
Will the reports go out every day automatically, without me initiating a report via the terminal? Thanks!

---

### Post by semijoyful on 2009-10-26
Not sure how to delete posts,so this one should be ignored:)
-Kirk

---

### Post by tetralectic on 2009-10-26
> [CHBlackElk]("http://ubuntuforums.org/member.php?u=932413"): I'm pretty sure I missed something. To tell the truth I'm new to linux and still very anxious to learn everything I can. So far this thread has answered everything for me except how to set it up to send from gmail. Like I said I may have missed something, I am a newbie, but I keep trying to send reports to test it and I the same error that's listed on the first page, and no email ever shows up. Is this my bad, or a bug?> [semijoyful]("http://ubuntuforums.org/member.php?u=370221"): I feel your pain. I too have some difficulty getting this thing to send through the mail. Of course I think it's just more n00b luck than anything else for me. Here's my output when I generate report:[semijoyful]("http://ubuntuforums.org/member.php?u=370221") I have no special insight into this program, I'm just a user, but when I look at the first few lines of your terminal output I see a difference with mine. You have
> [FONT=monospace]net-responsibility-report[6026]: Generating report
net-responsibility-report[6026]: Sending report
net-responsibility-report[6026]: SMTP is disabled. Sending report to standard out.
####################
## Startup Report ##
####################[/FONT]I have
> net-responsibility-report[1933]: Generating report
net-responsibility-report[1933]: Sending report
send: 'ehlo [127.0.1.1]\r\n'
reply: '250-mx.google.com at your service, ["My IP address"]\r\n'I'm struck by the "[FONT=monospace]SMTP is disabled. ...[/FONT]" line in your output. Does your Net Responsibilty configuation include the entry> What is your mail server's name? If you don't know, ask your ISP or e-mail provider. If you're using Postfix, enter localhost. [smtp.gmail.com] for the gmail smtp server?

Just a thought

---

### Post by semijoyful on 2009-10-27
Thanks for that.  I'll try it and post the results.
-Kirk

---

### Post by semijoyful on 2009-10-27
It worked!  Thanks for that simple tip, tetralectic. ::kudos::  To the developers,  I'm wondering if there's a way to make the report less verbose.  I used the sudo net-responsibility-report | less; however, nothing happened in the terminal.  My accountability partner may not have time to wade through all of that info.  Is there a way I can shorten it to just show the essentials: Startup, Shutdown, and the Hostnames on this Day?
Thanks for time,

Kirk

---

### Post by McMurdo on 2009-10-27
> **tetralectic said:**
> 
I know this belongs in another thread, if an approach to Covenant Eyes regarding submiting Net Responsibility logs to their excellent analysis software is rebuffed, I suspect we'll have more luck approaching x3watch since it's part of a church ministry with a focus on the harms cyber sex.

I think we still may have some success with Covenant Eyes, though. There is still some positive discussion going on (slowly) over at the CE blog post about [CE for Linux]("http://www.covenanteyes.com/blog/2009/06/10/covenant-eyes-for-linux/#comments"). Luke Gilkerson from CE even replied to one of my recent comments.

I have a thread going over [here]("http://ubuntuforums.org/showthread.php?t=1267544") about writing a letter to Covenant Eyes humbly requesting technical information so we could send reports to their servers.

---

### Post by tetralectic on 2009-10-27
> **McMurdo said:**
> Luke Gilkerson from CE even replied to one of my recent comments.
I just read his reply -- promising! :D  And thanks for drawing attention to the thread you started regarding writing a letter to Covenant Eyes.

A thought regarding the Net Responsibility launcher in the gnome panel. The command is "sudo net-responsibility-config-cli --standalone" which launches fine from the gnome panel, but when executed from Cairo dock it doesn't launch. There's an implicit "gnome-terminal" command in there that's recognized by the gnome panel, but not Cairo dock. How about changing the command from "sudo net-responsibility-config-cli --standalone" to "gnome-terminal -x sudo net-responsibility-config-cli --standalone" which executes nicely in both the gnome panel and Cairo dock?

---

### Post by Mickeyj4j on 2009-10-28
hi all I cant find the .deb package. I click the link to teh download page and it wants to download teh tar file..

when doing an internet search for net responsibility .deb download it gives this post mainly

where can I go from here. 

also I am using "linux mint 7 xfce ce" which is based on ubuntu 9.04 i think. 

it seems there is no .deb download package well not in the usual way 

I think net responsibility should think about creating its own website :p. there are free ones out there which you can use.
it would be handy then all the download files could be in one place and users could have a choice. 

for now I am going to use the tar file and do it the long way

---

### Post by roggan87 on 2009-10-28
Hi all!
I'm working on a new version of Net Responsibility, which is quite improved. It's not completely ready for testing, but it's coming ;)
I've just temporarily made a website (which will be the official home of Net Responsibility), where the very basic stuff are. Please visit [www.netresponsibility.com](www.netresponsibility.com).
I will keep up the work, and hopefully be able to present a new version soon. I'm sorry if I don't answer all the questions that appears here. I've been focusing on the developing, and unfortunately I'm no expert in debugging and stuff.

So, keep in touch, God bless

---

### Post by tetralectic on 2009-10-28
> **roggan87 said:**
> Hi all!
I'm working on a new version of Net Responsibility, which is quite improved. It's not completely ready for testing, but it's coming ;)
I've just temporarily made a website (which will be the official home of Net Responsibility), where the very basic stuff are. Please visit [www.netresponsibility.com]("http://www.netresponsibility.com").
I will keep up the work, and hopefully be able to present a new version soon. I'm sorry if I don't answer all the questions that appears here. I've been focusing on the developing, and unfortunately I'm no expert in debugging and stuff.

So, keep in touch, God bless

That's really cool, and I'm so looking forward to the new alpha. Many, many thanks for the work you are putting into this :D It might be worth mentioning on the web page that Net Responsibility is for linux boxes.

A quick mention again regarding the Net Responsibility configuration launcher in the gnome panel. The command is "sudo net-responsibility-config-cli --standalone" which launches fine from the gnome panel, but when executed from Cairo dock it doesn't launch. There's an implicit "gnome-terminal" command in there that's recognized by the gnome panel, but not Cairo dock. If this is still relevant to the forthcoming alpha, how about changing the command from "sudo net-responsibility-config-cli --standalone" to "gnome-terminal -x sudo net-responsibility-config-cli --standalone" which executes nicely in both the gnome panel and Cairo dock?

---

### Post by McMurdo on 2009-10-29
Apologies in advance for cross posting, but CE has posted [a job listing]("http://jobs.stackoverflow.com/default.asp?5498") mentioning Linux (not explicit CE for Linux, but it caught my eye on a google). I posted about it over [here]("http://ubuntuforums.org/showthread.php?p=8191091#post8191091"). This could very well be for their backend, but hey, I thought I'd mention it.

---

### Post by semijoyful on 2009-10-29
Great to see this shaping up so much!  I friendly request for the website is to include a link to the 64bit package too.  Thanks for all your hard work.  Have anybody doing any logo work for this thing?
-Kirk

---

### Post by tetralectic on 2009-10-29
> **semijoyful said:**
> ...  Thanks for all your hard work.  Have anybody doing any logo work for this thing?
-Kirk
Not to my knowledge, but the palm tree at the top of the web page is a nice touch.

---

### Post by semijoyful on 2009-10-30
I am happy to do some logo design work if you would like.  If it's needed...
-Kirk

---

### Post by roggan87 on 2009-10-30
> Great to see this shaping up so much! I friendly request for the website is to include a link to the 64bit package too. Thanks for all your hard work. Have anybody doing any logo work for this thing?

As far as I know, the "64 bit version" is the deb package on page 19, and I've uploaded it. It's under the link "If none of the above files are working for you, you may try this one."

Umm, not any more than what you see on the frontpage on netresponsibility.com. You can always give it a shot if you want to spice it up. I've done it in GIMP, and I can send you the xcf file if you'd like.

---

### Post by ArrSea on 2009-11-05
Hey All,

I am needing some help on Net Responsibility. I am not getting any reports sent to any e-mail address. Yes, I ran the "Configure Net Responsibility" file and set up an smtp server with all the correct settings. 

I would appreciate any help, and (to summarize), why am I not getting any reports?

Thanks,

ArrSea

---

### Post by McMurdo on 2009-11-05
While we're offering services, I could probably do some CSS work in a couple of weeks if it's wanted. I'm not an expert but I do know a bit.

---

### Post by roggan87 on 2009-11-05
Believe it or not, but the 2.0 alpha is available for download! Check out [www.netresponsibility.com](www.netresponsibility.com) and try it out. It's fully working for me on a Puppy Linux computer, and when running xubuntu 9.10 LiveCD.

There are still some improvement to be done on the website, and the most critical is to make a login system, so that you could change values later. You should also be able to control your own personal blacklist and whitelist here.

But that will come later. For the moment you can try the program, hopefully use it without any problems, and report if you're running into any bugs.

> While we're offering services, I could probably do some CSS work in a couple of weeks if it's wanted. I'm not an expert but I do know a bit.

Umm, yeah maybe. I'm no expert either, but I know a bit ;) Thanks for your offer, I'll contact you if I need any help.

One thing that I really could use some help with, is the language. You can all help me with spell checking, and formulations.

---

### Post by tetralectic on 2009-11-05
> **roggan87 said:**
> Believe it or not, but the 2.0 alpha is available for download! Check out [www.netresponsibility.com]("http://www.netresponsibility.com") and try it out. It's fully working for me on a Puppy Linux computer, and when running xubuntu 9.10 LiveCD.

...

For the moment you can try the program, hopefully use it without any problems, and report if you're running into any bugs..

Wow, wonderful news, and many thanks again for the work you have put into this. I have registered (I think) and installed (Ubuntu 9.10) the 2.0 alpha. The configuration was disconcertingly easy, it left me feeling that it should be it harder -- but that's a good thing :D

In the spirit of alpha testing, regarding registering: when I clicked on the activation link of the "Activate your account" E-mail I received from "activate@netresponsibility.com" I was sent to the web page "http://www.netresponsibility.com/activate.php?username=tetralectic&confirm=a7067ee14e7ee9a969f55fbffca528ed". The web page was blank however, except for the line "No input file specified."; clearly a web site bug. I'm though left wondering if I successfully activated my Net Responsibility account.

All in all, pretty cool!\\:D/

---

### Post by roggan87 on 2009-11-06
> In the spirit of alpha testing, regarding registering: when I clicked on the activation link of the "Activate your account" E-mail I received from "activate@netresponsibility.com" I was sent to the web page "http://www.netresponsibility.com/activate.php?username=tetralectic&confirm=a7067ee1 4e7ee9a969f55fbffca528ed". The web page was blank however, except for the line "No input file specified."; clearly a web site bug. I'm though left wondering if I successfully activated my Net Responsibility account.

I'm very sorry about that! I've sent you a personal message with instructions. And for everyone else, I believe the problem is corrected, and that it's now working again.

---

### Post by tetralectic on 2009-11-06
> **roggan87 said:**
> I'm very sorry about that! I've sent you a personal message with instructions. And for everyone else, I believe the problem is corrected, and that it's now working again.

Hi Roggan87

I just tried a couple of times to send you a personal message, but my sent message folder doesn't seem to have a record of it, so I'm posting it here.

I clicked on the link you sent me in the private message and was sent to a web page where I filled in my password and clicked the activate button :D. I was the sent to the web page "http://www.netresponsibility.com/confirm.php" which was blank except for the now familiar message "No input file specified." :icon_frown:. Sadly, I'm still left wondering if my registration succeeded :confused:?

---

### Post by tetralectic on 2009-11-08
The activation required for new alpha is now working \\:D/
Many thanks Roggan87 =D>

---

### Post by ArrSea on 2009-11-09
> **roggan87 said:**
> Believe it or not, but the 2.0 alpha is available for download! Check out [www.netresponsibility.com]("http://www.netresponsibility.com") and try it out. It's fully working for me on a Puppy Linux computer, and when running xubuntu 9.10 LiveCD.

There are still some improvement to be done on the website, and the most critical is to make a login system, so that you could change values later. You should also be able to control your own personal blacklist and whitelist here.

But that will come later. For the moment you can try the program, hopefully use it without any problems, and report if you're running into any bugs.



Umm, yeah maybe. I'm no expert either, but I know a bit ;) Thanks for your offer, I'll contact you if I need any help.

One thing that I really could use some help with, is the language. You can all help me with spell checking, and formulations.

Sure, I'd be glad to help! Honest, just having this program makes me so happy, and the fact that it's free? I love it!

Just tell me how to help, I'd love to spell-check and all that. 

-ArrSea

---

### Post by ArrSea on 2009-11-09
Just a positive report, I just did a fresh install of Net Responsibility 2.0 on Ubuntu 9.10, and registered with no problem! 

-ArrSea

---

### Post by roggan87 on 2009-11-09
Glad to hear it's working guys!
I'm going away for a week, so I might be late to answer...

---

### Post by sadastronaut on 2009-11-13
I'm using the latest alpha version 2.0.  Is there a way to change settings once it has been configured on the netresponsibility.com website?  Particularly, I would like to change my password.  Thanks.

---

### Post by roggan87 on 2009-11-17
> I'm using the latest alpha version 2.0. Is there a way to change settings once it has been configured on the netresponsibility.com website? Particularly, I would like to change my password. Thanks.

Hi! I'm glad you're using the latest alpha version. Unfortunately there is no way to change settings yet, but that's the first thing on my todo list. So far, you can send me a personal message with the settings you'd like to change, and I'll fix it.

---

### Post by Mickeyj4j on 2009-11-18
where is a tutoral on how to use this eg how to send report ( i would prefer it to be automatic. like XXXChurch now that is the best application i have seen 
'

---

### Post by tetralectic on 2009-11-19
> **Mickeyj4j said:**
> where is a tutoral on how to use this eg how to send report ( i would prefer it to be automatic. like XXXChurch now that is the best application i have seen 
'Currently there is no tutorial on Net Responsibility, but it's quite simple to use. This forum, and the people here are, for the moment, the knowledge repository. The application is still at an alpha stage of development, but it is the only accoutability application for Linux that's under active development (many thanks to mssever and roggan87). It is quite like X3Watch, will mail out reports with an interval of your choosing, and can be downloaded from [www.netresponsibility.com]("http://www.netresponsibility.com"). You will have to activate an account for the software to work.

---

### Post by Mickeyj4j on 2009-11-22
> **tetralectic said:**
> Currently there is no tutorial on Net Responsibility, but it's quite simple to use. This forum, and the people here are, for the moment, the knowledge repository. The application is still at an alpha stage of development, but it is the only accoutability application for Linux that's under active development (many thanks to mssever and roggan87). It is quite like X3Watch, will mail out reports with an interval of your choosing, and can be downloaded from [www.netresponsibility.com]("http://www.netresponsibility.com"). You will have to activate an account for the software to work.

ok so how can i do all this i have installed and set it up with my contacts now what ??????

---

### Post by Mickeyj4j on 2009-11-23
HELP what does this mean i think it means that there is an error what could it be. 

meowmint@meowmint-desktop ~ $ sudo net-responsibility-report
[sudo] password for meowmint: 
net-responsibility-report[9719]: Generating report
net-responsibility-report[9719]: Sending report
send: 'ehlo [127.0.1.1]\r\n'
reply: '250-mx.google.com at your service, [121.98.187.36]\r\n'
reply: '250-SIZE 35651584\r\n'
reply: '250-8BITMIME\r\n'
reply: '250-STARTTLS\r\n'
reply: '250-ENHANCEDSTATUSCODES\r\n'
reply: '250 PIPELINING\r\n'
reply: retcode (250); Msg: mx.google.com at your service, [121.98.187.36]
SIZE 35651584
8BITMIME
STARTTLS
ENHANCEDSTATUSCODES
PIPELINING
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 87, in <module>
    s.login(smtpinfo['login_name'], smtpinfo['password'])
  File "/usr/lib/python2.6/smtplib.py", line 552, in login
    raise SMTPException("SMTP AUTH extension not supported by server.")
smtplib.SMTPException: SMTP AUTH extension not supported by server.
net-responsibility-report[9719]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[9719]: /usr/lib/ruby/1.8/sqlite3/errors.rb:62:in 'check': Unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[9719]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:121:in 'close'
net-responsibility-report[9719]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[9719]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[9719]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/report_mailer.rb:83:in `send_message': send-report.py exited due to an unhandled exception. (RuntimeError)
	from /usr/share/net-responsibility/lib/report_mailer.rb:93:in `create_and_send'
	from /usr/local/bin/net-responsibility-report:89:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119
meowmint@meowmint-desktop ~ $ 


if you can help i would appreciate it

---

### Post by tetralectic on 2009-11-23
> **Mickeyj4j said:**
> HELP what does this mean i think it means that there is an error what could it be. 

meowmint@meowmint-desktop ~ $ sudo net-responsibility-report
[sudo] password for meowmint: 
net-responsibility-report[9719]: Generating report
net-responsibility-report[9719]: Sending report
send: 'ehlo [127.0.1.1]\r\n'
reply: '250-mx.google.com at your service, [121.98.187.36]\r\n'
reply: '250-SIZE 35651584\r\n'

...

if you can help i would appreciate it

What version of net responsibility have you installed, 0.6 or 2.0?

---

### Post by Carl Hamlin on 2009-11-29
> **mssever said:**
> I've been working on an Internet accountability program for Linux. The idea is to log the websites you visit, then periodically e-mail that log so someone else.

Why?

---

### Post by jonathonblake on 2009-11-29
> **Carl Hamlin said:**
> Why?
That is what accountability software does.

jonathon

---

### Post by Carl Hamlin on 2009-11-30
> **jonathonblake said:**
> That is what accountability software does.

jonathon

*grin*

Thank you for clarifying, I think...

I guess I'm not sure why I would necessarily need to be held 'accountable' to anyone other than myself for my viewing habits. Is this software for children's systems, so parents can monitor their web usage? Something like that?

---

### Post by Dragonbite on 2009-11-30
> **Carl Hamlin said:**
> *grin*

Thank you for clarifying, I think...

I guess I'm not sure why I would necessarily need to be held 'accountable' to anyone other than myself for my viewing habits. Is this software for children's systems, so parents can monitor their web usage? Something like that?

For kids, yeah a monitoring system like this would not be a bad idea. It goes beyond just blocking or can be in place of blocking, leaving the kids up to the chance to "make the right decision".

Internet addiction and/or porn addiction is an affliction that ruins many relationships. If somebody were seriously trying to avoid using the internet as such, a system that they cannot change which emails a person set as a "guardian", or somebody to be hold the person accountable can be a great therapy aid.

What about for sex offenders on parole?

At least, this is from my understanding.

---

### Post by jsjones on 2009-12-10
Thanks for all the effort on this great project, it's exactly what I have been looking for.  Just started following this thread a few weeks ago, so not sure if this has been asked before, but I'm a little curious how this would work on a netbook, or any computer that will be turned off and on regularly.

My understanding is that if the daemon is stopped, the accountability partner will receive notice.  Does the application distinguish between manually stopping the daemon (to intentionally disable the application) and the system stopping the daemon (ie, on shut-down, reboot, etc).  I wouldn't want the accountability partner receiving notice every time the daemon was stopped due to shut-down, which could occur several times a day maybe.  Is the there a distinction?

Thanks again for filling this void.

---

### Post by roggan87 on 2009-12-13
> Thanks for all the effort on this great project, it's exactly what I have been looking for. Just started following this thread a few weeks ago, so not sure if this has been asked before, but I'm a little curious how this would work on a netbook, or any computer that will be turned off and on regularly.

My understanding is that if the daemon is stopped, the accountability partner will receive notice. Does the application distinguish between manually stopping the daemon (to intentionally disable the application) and the system stopping the daemon (ie, on shut-down, reboot, etc). I wouldn't want the accountability partner receiving notice every time the daemon was stopped due to shut-down, which could occur several times a day maybe. Is the there a distinction?

Hi jsjones!
You don't have to worry. Net Responsibility sends a report once a day (the versions up to 0.6.0), and if you choose to install the Net Responsibility 2.0 alpha (which I hope you do), then you can set the interval of days between reports. 

Good luck, and please let us know if you need some help!

---

### Post by thovmas on 2009-12-14
Net Responsibility 2.0 isn't sending reports from Ubuntu 9.04
I set it on daily to test it out, but it's the third day and nothing has
happened. What can I do?
Thanks!

---

### Post by CAPLinux on 2009-12-14
Roggan87

I installed the 2.0 alpha a few weeks ago and set the site to email weekly to my accountability partners and myself.  I haven't received any reports at all.  What could I be doing wrong here?

---

### Post by roggan87 on 2009-12-14
> Net Responsibility 2.0 isn't sending reports from Ubuntu 9.04
I set it on daily to test it out, but it's the third day and nothing has
happened. What can I do?
Thanks! 

> Roggan87

I installed the 2.0 alpha a few weeks ago and set the site to email weekly to my accountability partners and myself. I haven't received any reports at all. What could I be doing wrong here?

Hi guys!

I'm really sorry about this. I've installed Kubuntu 9.10 on my own computer, and I experience the same problem. I'll have a look at it, and try to fix it as soon as possible. In the meantime, you can run the command ```
sudo net-responsibility-report
```
once in a while to send the reports manually, but I know this has to be fixed.

Thanks for sharing this very useful info!

---

### Post by roggan87 on 2009-12-14
Hi!

I've uploaded a new alpha version with some bugfixes. I've also added a feature, called testmail. If you run the command ```
sudo net-responsibility-report --testmail
``` then you will receive a mail to your own mail address. This is only to check that the program is set up and working correctly.

There are still some other bugs to work with, such as automatic reports. But hopefully this is a little better.

Good night, zzz...

---

### Post by CAPLinux on 2009-12-15
Roggan,

I downloaded the file from the netresponsibility.com web site.  Was this the right location for the upgraded 2.0 client?  I ran the --testmail command and haven't gotten a reponse back.

---

### Post by tetralectic on 2009-12-15
> **roggan87 said:**
> Hi!

I've uploaded a new alpha version with some bugfixes. I've also added a feature, called testmail. If you run the command ```
sudo net-responsibility-report --testmail
``` then you will receive a mail to your own mail address. This is only to check that the program is set up and working correctly.

There are still some other bugs to work with, such as automatic reports. But hopefully this is a little better.

Good night, zzz...
> **CAPLinux said:**
> Roggan,

I downloaded the file from the netresponsibility.com web site. Was this the right location for the upgraded 2.0 client? I ran the --testmail command and haven't gotten a reponse back.
Hi Roggan87

I also have downloaded the new 2.0 alpha from netresponsibility.com. The .deb is a different size from previous so it's a new version. :)

Sadly I too am having the same problem as CAPLinux. If I run ```
sudo net-responsibility-report --testmail
``` or ```
sudo net-responsibility-report
``` no responses or reports are sent out :(

This is my terminal output using the --testmail option ```
appleseed@Appleseed:~$ sudo net-responsibility-report --testmail
Downloading the configurationfile...
Loading it.
Downloading blacklist for Porn
Downloading blacklist for Pornstars
Downloading blacklist for Models
Downloading blacklist for Celebrities
Downloading blacklist for Pornstars_extended
/usr/share/net-responsibility/lib/options.rb:228:in `update_settings': private method `gsub!' called for nil:NilClass (NoMethodError)
    from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
    from /usr/local/bin/net-responsibility-report:79:in `new'
    from /usr/local/bin/net-responsibility-report:79:in `initialize'
    from /usr/local/bin/net-responsibility-report:131:in `new'
    from /usr/local/bin/net-responsibility-report:131
``` I get the same output ```
appleseed@Appleseed:~$ sudo net-responsibility-report
Downloading the configurationfile...
Loading it.
Downloading blacklist for Porn
Downloading blacklist for Pornstars
Downloading blacklist for Models
Downloading blacklist for Celebrities
Downloading blacklist for Pornstars_extended
/usr/share/net-responsibility/lib/options.rb:228:in `update_settings': private method `gsub!' called for nil:NilClass (NoMethodError)
    from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
    from /usr/local/bin/net-responsibility-report:79:in `new'
    from /usr/local/bin/net-responsibility-report:79:in `initialize'
    from /usr/local/bin/net-responsibility-report:131:in `new'
    from /usr/local/bin/net-responsibility-report:131
``` without the --testmail option.

Thanks again for your work on this needed app.

---

### Post by martinquested on 2009-12-18
I installed the 2.0a.deb but then run into a bug: please advise!

$ sudo net-responsibility-config-cli
/usr/local/bin/net-responsibility-config-cli:90:in `initialize': undefined method `online_user' for #<Options:0xb79c85bc> (NoMethodError)
        from /usr/local/bin/net-responsibility-config-cli:158:in `new'
        from /usr/local/bin/net-responsibility-config-cli:158

---

### Post by roggan87 on 2009-12-18
> I downloaded the file from the netresponsibility.com web site. Was this the right location for the upgraded 2.0 client? I ran the --testmail command and haven't gotten a reponse back.

> This is my terminal output using the --testmail option
Code:
...

Hi!

This was a bug on the website, try again, hopefully it'll work now.
Please let me know if it doesn't. 

> I installed the 2.0a.deb but then run into a bug: please advise!

$ sudo net-responsibility-config-cli
/usr/local/bin/net-responsibility-config-cli:90:in `initialize': undefined method `online_user' for #<Options:0xb79c85bc> (NoMethodError)
from /usr/local/bin/net-responsibility-config-cli:158:in `new'
from /usr/local/bin/net-responsibility-config-cli:158

Hmm... This was strange. Do you have the file /etc/net-responsibility.conf, and if so, paste the content here.

Thanks a lot for your patience and bug reporting!

Roggan

---

### Post by martinquested on 2009-12-19
Yes, I do have that file.  It appears still to have the old settings from version 0.5.  I've snipped out the personal info...

---
# This is the configuration file for Net Responsibility.
# It is in YAML format; the syntax should be quite obvious. If you need
# more details, see <http://yaml.org>.

# What is your name? At a minimum, Net Responsibility uses your name
# when sending reports.
name: Martin Q

# What e-mail address should reports come from? Change this to your
# e-mail address.
email_from: ***snip***

# List here the e-mail address(es) to receive reports. For example:
# email_to:
#   - [email]email@somedomain.com[/email]
#   - [email]another@email.com[/email]
email_to:
  - ***snip***

# Configure the server to use for sending e-mail. The pre-sets are for
# Postfix. If you use some other e-mail, fill this section in with the
# details provided by your e-mail provider or ISP.
#
# Once you've configured this section, set use_smtp to true.
smtp_server:
  use_smtp      : true      # Set to true when configured
  server        : smtp.googlemail.com # localhost if you're using postfix
  port          : 587        # Default port: 25
  authentication: true # Whether this server requires authentication. Possible values: true, false
  use_tls       : true # Does this host require TLS encryption? Possible values: true, false
  login_name    : ***snip***
  password      : ***snip***

# The location of the logfile and pidfile must be specified, else Net
# Responsibility will refuse to start.
# WARNING: Don't change these unless you know what you're doing!
logfile: /var/log/net-responsibility.log
pidfile: /var/run/net-responsibility.pid

---

### Post by User3k on 2009-12-19
I am just wondering something. I may have missed this, there are a lot of pages here and I haven't gone through them all. I know what this program does. But what is the point of this program? Is it only for parents to keep an eye on what their kids are doing?

---

### Post by martinquested on 2009-12-19
No, also those who, for reasons of personal integrity, want to make themselves accountable to a trusted friend over their use of their internet connection.

---

### Post by User3k on 2009-12-19
> **martinquested said:**
> No, also those who, for reasons of personal integrity, want to make themselves accountable to a trusted friend over their use of their internet connection.

Ok, cool. Thanks for clarifying that for me.

---

### Post by roggan87 on 2009-12-21
> Yes, I do have that file. It appears still to have the old settings from version 0.5. I've snipped out the personal info...

As you say, this is the old file from the 0.5 version. Are you sure you've installed the 2.0 alpha? Please run 
```
sudo net-responsibility-report --version
```

---

### Post by martinquested on 2009-12-21
Apparently this is version 2.0a and not 0.5, despite the 0.5 config file...

```

$ sudo net-responsibility-report --version
Net Responsibility 2.0a
Copyright 2007-2009 by Scott Severance & Robert Johansson

Net Responsibility is free software. You may distribute
it under the terms of the GNU General Public License,
version 2 or (at your option) any later version. Net
Responsibility carries no warranty of any kind.

```

---

### Post by roggan87 on 2009-12-22
> Apparently this is version 2.0a and not 0.5, despite the 0.5 config file...
Hmm... Try to reinstall the net-responsibility package. It might help. I'm not sure if this is a bug in the software, or just a coincident?

---

### Post by kfrancis on 2009-12-28
I know others have been having this same problem re: emailing of reports to accountability partners, but wanted to include myself with this thread: I have downloaded Net Responsibility onto my systems and set-up accountability partner emails. The first email report came thru without a problem but have since to see another report since I set-up the program over a week ago (I set the email reporting to once every other day). Any ideas?

Thanks.

---

### Post by tetralectic on 2009-12-28
> **kfrancis said:**
> I know others have been having this same problem re: emailing of reports to accountability partners, but wanted to include myself with this thread: I have downloaded Net Responsibility onto my systems and set-up accountability partner emails. The first email report came thru without a problem but have since to see another report since I set-up the program over a week ago (I set the email reporting to once every other day). Any ideas?

Thanks.

Hi kfrancis

The automatic reports feature is not working right now, a bug that Roggan87 is working on. He suggests that you send out reports manually for right now by typing at the command line
```
sudo net-responsibility-report
```

---

### Post by ArrSea on 2009-12-30
Just wanted to chime in and say, sadly, I'm also having trouble with Net Responsibility.
I've never got it to send out any reports, in the old 0.5.0 version, or the new 2.0a version.
When I run ```
sudo net-responsibility-report
[sudo] password for ----: 
Downloading the configurationfile...
Loading it.
Downloading blacklist for Porn
Downloading blacklist for Pornstars
Downloading blacklist for Models
Downloading blacklist for Celebrities
/usr/share/net-responsibility/lib/options.rb:204:in `update_settings': undefined method `join' for nil:NilClass (NoMethodError)
    from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
    from /usr/local/bin/net-responsibility-report:79:in `new'
    from /usr/local/bin/net-responsibility-report:79:in `initialize'
    from /usr/local/bin/net-responsibility-report:129:in `new'
    from /usr/local/bin/net-responsibility-report:129
```

I get that error. 

Also, Roggan87, what do you think about setting up a Launchpad or Bugzilla bug tracker for all the bugs we've been reporting? Would that help you?
I think it would help us users, so that we could see easilythe bugs that have been reported. (rather than paging thru page after page on the forum) :-)

Anyway, just wanted to say thanks, hope we can get this working.

-ArrSea

---

### Post by tetralectic on 2009-12-30
> **ArrSea said:**
> Just wanted to chime in and say, sadly, I'm also having trouble with Net Responsibility.
I've never got it to send out any reports, in the old 0.5.0 version, or the new 2.0a version.
When I run ```
sudo net-responsibility-report
[sudo] password for ----: 
Downloading the configurationfile...
Loading it.
Downloading blacklist for Porn
Downloading blacklist for Pornstars
Downloading blacklist for Models
Downloading blacklist for Celebrities
/usr/share/net-responsibility/lib/options.rb:204:in `update_settings': undefined method `join' for nil:NilClass (NoMethodError)
    from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
    from /usr/local/bin/net-responsibility-report:79:in `new'
    from /usr/local/bin/net-responsibility-report:79:in `initialize'
    from /usr/local/bin/net-responsibility-report:129:in `new'
    from /usr/local/bin/net-responsibility-report:129
```I get that error. 

Also, Roggan87, what do you think about setting up a Launchpad or Bugzilla bug tracker for all the bugs we've been reporting? Would that help you?
I think it would help us users, so that we could see easilythe bugs that have been reported. (rather than paging thru page after page on the forum) :-)

Anyway, just wanted to say thanks, hope we can get this working.

-ArrSea
Hi ArrSea

Have you tried downloading the latest 2.0a .deb file from the website? I was getting that error, but then Roggan87 fixed it and uploaded a new .deb file. It works for me now when I manually send out reports, but the automatic reporting feature is still broken.

tetralectic

---

### Post by roggan87 on 2010-01-05
Hi!

Sorry for being late to answer. Tetralectic, thanks for your input, I just want to confirm it ;) I'm working on the automatic response, and you should try the latest 2.0a version. If you have the latest version, you should be able to run:

```
sudo net-responsibility-report --testmail
```

> Also, Roggan87, what do you think about setting up a Launchpad or Bugzilla bug tracker for all the bugs we've been reporting? Would that help you?
I think it would help us users, so that we could see easilythe bugs that have been reported. (rather than paging thru page after page on the forum) 

I haven't thought about that, but I'm sure it would be a great help. I don't have any experience of such tools, but launchpad seemed to fit the needs very well. Anybody who wants to set up an account?

---

### Post by ArrSea on 2010-01-05
I'd be happy to set up an account, but I'm not sure what elements of Launchpad we'd want. A bugtracker, yes, (IMO), what about a [mailing list]("https://launchpad.net/+tour/community")? Or is that too much?
Launchpad also has [code hosting, version control]("https://launchpad.net/+tour/branch-hosting-tracking"), etc.
Do we need that? (I don't know, as personally I'm not a programmer, just a guy who loves computers). 
They also make it easy for the software to be [translated]("https://launchpad.net/+tour/translation").
It'd also track release dates, etc. Check out Launchpad for more details. [http://launchpad.net](http://launchpad.net)

Please comment on this, that way we can sort of figure out what we need?

I am so glad for this forum, but maybe it's time to expand a little. Just a thought. Feel free to disagree!

-ArrSea

---

### Post by martinquested on 2010-01-06
Hi,

I discovered that my package manager was not replacing the /etc/net-responsibility.conf file but instead saving the new file as /etc/net-responsibility.conf.dpkg-dist - in order to get the installation working I had to delete the old file *and* move the .dpkg-dist file into its place:

```

sudo rm /etc/net-responsibility.conf
sudo mv /etc/net-responsibility.conf.dpkg-dist /etc/net-responsibility.conf

```

Then an uninstall and install of the new package, and it works.


Now, a feature request:
A user-defined blacklist and whitelist.  Looking at the way the system currently works, this must be a relatively easy thing to implement, but would be a change to your server, not the client - right?

Thanks for all your work on this.

---

### Post by roggan87 on 2010-01-07
> I'd be happy to set up an account, but I'm not sure what elements of Launchpad we'd want. A bugtracker, yes, (IMO), what about a mailing list? Or is that too much?
Launchpad also has code hosting, version control, etc.
Do we need that? (I don't know, as personally I'm not a programmer, just a guy who loves computers).
They also make it easy for the software to be translated.
Hmm... Is it possible to start with bugtracking, and expand with other features if we want to? The very best thing would be to use netresponsibility.com as much as possible, as the only place to look for info about Net Responsibility. I only find it to be a little too much to work on the website, when the software isn't complete.

> I discovered that my package manager was not replacing the /etc/net-responsibility.conf file but instead saving the new file as /etc/net-responsibility.conf.dpkg-dist - in order to get the installation working I had to delete the old file *and* move the .dpkg-dist file into its place:
Glad you found the reason! I don't know if there's anything to do about the package, or if it has to be this way?

> Now, a feature request:
A user-defined blacklist and whitelist. Looking at the way the system currently works, this must be a relatively easy thing to implement, but would be a change to your server, not the client - right?
You're right! The only thing left to do, to be able to use these features, is to edit the website. We just need a good way to add/delete/edit the personal blacklist and whitelist. I'll take a look at this. Some features are almost working, I just have to make them work completely.

Thanks for your patience and feedback!

---

### Post by merlin114 on 2010-01-09
Thanks for making this wonderful tool for Ubuntu.  Aside from the emails, is there a way to view the log files directly?  If it is a text file, where can I find it?

---

### Post by merlin114 on 2010-01-12
I have an idea for a feature: it would be good to have the reported websites tagged with date/time. When multiple folks are using the computer, if a warning is flagged, it would be good to track down who was on the computer at that time.

---

### Post by roggan87 on 2010-01-12
> I have an idea for a feature: it would be good to have the reported websites tagged with date/time. When multiple folks are using the computer, if a warning is flagged, it would be good to track down who was on the computer at that time.
Good idea. This feature was implemented in the 0.5 version, but I erased it to make the mail more compact. It would be good to choose if you want it or not.

---

### Post by roggan87 on 2010-01-12
Hey, one thing came to my mind.
If you're tired of running net-responsibility-report manually, you can use this command to make it happen once every week:
```
sudo ln -s /usr/share/net-responsiblity/net-responsibility-report /etc/cron.weekly/net-responsibility-report
```
You can also replace "cron.weekly" with "cron.daily", "cron.monthly" or "cron.hourly".

---

### Post by ArrSea on 2010-01-12
@roggan87 
Quick question. Launchpad wants to know what license Net Responsibility is under. 
I don't know, it's not listed on the webpage (should we add it to the web page?).
Is GPL v3 okay with you and mssever?
I'll wait for your answer...

---

### Post by roggan87 on 2010-01-13
> @roggan87
Quick question. Launchpad wants to know what license Net Responsibility is under.
I don't know, it's not listed on the webpage (should we add it to the web page?).
Is GPL v3 okay with you and mssever?
I'll wait for your answer...

There's a lot of info that should be on the webpage. I'll quote mssever:
> # This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2 of the
# License, or (at your option) any later version.

I'd say, choose GPL v2. Not sure if it will make any difference. Correct me if I'm wrong, but GPL v2 is what mssever chose in the first place.

---

### Post by ArrSea on 2010-01-14
Sure, GPLv2 it is then. Thanks!

-ArrSea

Oh, and thanks for the tip about "cron.weekly" I think I'll try that.

---

### Post by ArrSea on 2010-01-14
Ok, here it is everyone!
Net Responsibility has its very own Launchpad page now!
Check it out at: [https://launchpad.net/netresponsibility](https://launchpad.net/netresponsibility)

You can submit a bug report or ask a question!

This way it will be a whole lot easier to see all the bugs submitted, without having to browse through a dozen pages on the forum!

So, if you have a bug to report, go to [https://bugs.launchpad.net/netresponsibility](https://bugs.launchpad.net/netresponsibility)
and click "Report a bug"

Thanks!

-ArrSea

---

### Post by tetralectic on 2010-01-14
> **ArrSea said:**
> Ok, here it is everyone!
Net Responsibility has its very own Launchpad page now!
Check it out at: [https://launchpad.net/netresponsibility](https://launchpad.net/netresponsibility)

You can submit a bug report or ask a question!

This way it will be a whole lot easier to see all the bugs submitted, without having to browse through a dozen pages on the forum!

So, if you have a bug to report, go to [https://bugs.launchpad.net/netresponsibility](https://bugs.launchpad.net/netresponsibility)
and click "Report a bug"

Thanks!

-ArrSea

Thanks ArrSea and Roggan87, it's good to see Net Responsibility with its own launchpad page

:)

---

### Post by kfrancis on 2010-01-19
Having issues with reports being sent out per my requested frequency. The initial report was sent then none after that. I went ahead and logged this bug under Launchpad as well. Thanks for any help you can provide.

---

### Post by Mickeyj4j on 2010-01-23
Is there a more gtk interface for net responsibility. 

I find that net responsibility is not that good as it will not send reports unless I tell it to. even though I set it to send them weekly. i need this as help. what good is this application for if it never does what it clams to do. 

Maybe i dont really know how to use it properly. 

on the other hand when I had xp I was using xxxChurch which worked easily and flawlessly. y dont they just get a ubuntu version.

---

### Post by tetralectic on 2010-01-23
> **Mickeyj4j said:**
> Is there a more gtk interface for net responsibility. 

I find that net responsibility is not that good as it will not send reports unless I tell it to. even though I set it to send them weekly. i need this as help. what good is this application for if it never does what it clams to do. 

Maybe i dont really know how to use it properly. 

on the other hand when I had xp I was using xxxChurch which worked easily and flawlessly. y dont they just get a ubuntu version.

Hi Mickeyj4j

> what good is this application for if it never does what it clams to doActually it does do what it claims. Net Responsibility 2.0a claims that it's an alpha, meaning that many things don't work properly yet, it's a work in progress. With commercial closed source software you'll never see an alpha. Releasing an alpha version is something that is done in open source software so that one can benefit from the capabilities it does have, however flawed the alpha is. I use 2.0a with manual reports so that my accountability partners benifit from it's ability to analyse reports. The 0.5 version is a beta and I found it's automatic reporting reliable once the mailing options were properly configured. It was just hard for my accountability partners having to sift through all my web surfing.

I agree that x3watch is an excellent piece of software, I've used it myself, but in it's absence on Linux I'm just really grateful that [mssever]("http://ubuntuforums.org/member.php?u=126210"), roggan87 and ArrSea are volunteering their time, energy and expertise to fill this need.

---

### Post by Mickeyj4j on 2010-01-25
> **tetralectic said:**
> Hi Mickeyj4j

Actually it does do what it claims. Net Responsibility 2.0a claims that it's an alpha, meaning that many things don't work properly yet, it's a work in progress. With commercial closed source software you'll never see an alpha. Releasing an alpha version is something that is done in open source software so that one can benefit from the capabilities it does have, however flawed the alpha is. I use 2.0a with manual reports so that my accountability partners benifit from it's ability to analyse reports. The 0.5 version is a beta and I found it's automatic reporting reliable once the mailing options were properly configured. It was just hard for my accountability partners having to sift through all my web surfing.

I agree that x3watch is an excellent piece of software, I've used it myself, but in it's absence on Linux I'm just really grateful that [mssever]("http://ubuntuforums.org/member.php?u=126210"), roggan87 and ArrSea are volunteering their time, energy and expertise to fill this need.


ok maybe thats so but i gave up when i did everything that i was ment to, to the letter, and nothing ever worked. my friend never received mail(unless i told it to send it) but that was like several months and maybe versions ago.

---

### Post by jessethouin on 2010-01-26
This is an incredible effort.  I had been working on my own home-grown version using a kludge of tcpdump and huge hosts lists, but this effort is so much farther along than I would be on my own.

Regardless of the technology used to capture and report web usage, the Linux platform presents a fatal flaw to the true addict (who will do anything and everything for a 'hit'): anyone with root access can easily manipulate the system to avoid being caught.

And this is where I stopped my own personal development.  I realized that in order to truly make this work, we (the community) need to use a bit of social engineering.  This is my question:

Is there a way to make a process unkillable, or at least report that it had been killed (with kill -9 for example)?  I see many ways around Net Responsibility (as well as my own efforts), and I'm concerned that a desperate addict would figure a way around being held accountable.

Jesse
[http://www.samsonsociety.org/profile/JesseThouin]("http://www.samsonsociety.org/profile/JesseThouin")

---

### Post by roggan87 on 2010-01-26
Hi Jesse!

> This is an incredible effort. I had been working on my own home-grown version using a kludge of tcpdump and huge hosts lists, but this effort is so much farther along than I would be on my own.
Thanks, glad you like it :)

> Is there a way to make a process unkillable, or at least report that it had been killed (with kill -9 for example)? I see many ways around Net Responsibility (as well as my own efforts), and I'm concerned that a desperate addict would figure a way around being held accountable.
Originally, Scott Severance created this program, and maintained it up to version 0.6.0. Then I started to improve it, and Scott kind of retired. I know that he's been working on this. The program does report if you try to kill it manually, but of course this is something that can be improved.
I certainly don't think it's possible to make a process unkillable.

The goal is that Net Responsibility would be impossible to get around, but there are still flaws. The less people know about these, the better. I use this program for accountability, but I've also promised to admit, to confess if I would try to manipulate or shut down the program manually. The program is a help, but it's not the ultimate solution.

BTW, do you do any programming?

---

### Post by mssever on 2010-01-27
Some of you may be quite surprised to see me here again! :) I've been very busy the last year or so and haven't had time for any programming. I've occasionally read comments on this thread, but I haven't had time to be involved. Thanks to roggan87 for taking over this project.

> **jessethouin said:**
> Is there a way to make a process unkillable, or at least report that it had been killed (with kill -9 for example)?  I see many ways around Net Responsibility (as well as my own efforts), and I'm concerned that a desperate addict would figure a way around being held accountable.
I posted because I wanted to reply to this question. As far as I know, it isn't possible to log a SIGKILL unless you hack around in the kernel. The thing is, SIGKILL causes the kernel to terminate the process without sending any signals to the process. Thus, there's nothing for the process to trap, and the process doesn't know it's about to die.

I can think of one workaround, though, in case your computer is accessible to more than one person:
[LIST=1]
[*]Create another user account and give it full sudo rights.
[*]Configure sudo to deny your user access to the visudo and kill commands. You can write wrapper programs if necessary, provided they're only writable by the second user.
[*]Give the trusted second party the second account and have him/her change the password.
[*]Make sure the root account is disabled (as is the default in Ubuntu).
[/LIST]This might not be ideal, but it's the only workaround I know of.

---

### Post by McMurdo on 2010-01-28
> **mssever said:**
> 

I can think of one workaround, though, in case your computer is accessible to more than one person:
[LIST=1]
[*]Create another user account and give it full sudo rights.
[*]Configure sudo to deny your user access to the visudo and kill commands. You can write wrapper programs if necessary, provided they're only writable by the second user.
[*]Give the trusted second party the second account and have him/her change the password.
[*]Make sure the root account is disabled (as is the default in Ubuntu).
[/LIST]This might not be ideal, but it's the only workaround I know of.

Yeah, but still: shut off computer, boot from a CD, wipe partition, reinstall (or just run from the CD for that matter and then switch back to Linux on the hard drive). Really an unsolvable matter in regards to software (including Windows or Mac... the suffer from the same problem of being able to be bypassed by use of another OS).

---

### Post by ArrSea on 2010-01-28
> **McMurdo said:**
> Yeah, but still: shut off computer, boot from a CD, wipe partition, reinstall (or just run from the CD for that matter and then switch back to Linux on the hard drive). Really an unsolvable matter in regards to software (including Windows or Mac... the suffer from the same problem of being able to be bypassed by use of another OS).
Yes, this is true. I think that's why it ultimately comes down to a person's heart. If you want to find a way around it, you probably can. That's the whole purpose for accountability; having others in your life who care enough about you to hold you accountable and help you. 

Because honestly, if you really wanted to, you could just pop in a live CD of some Linux distro, and surf away. Anyway, I don't mean to get on a soapbox or anything, and you're welcome to disagree with my position. 

-ArrSea

---

### Post by mssever on 2010-01-30
I think jessethouin's point remains valid. There are some people who need tougher accountability standards and who would benefit from having a system that can't be bypassed without leaving a trace.

The workaround I mentioned, as far as I can tell, will work fully provided the user is running that particular OS install--although there might need to be a few more programs that are restricted via sudoers.

For the case of booting into another OS, you can tell grub to require a password (known in this case only to an accountability partner) before booting any non-default OS. Additionally, the BIOS settings can be adjusted to not allow booting from a CD (or flash drive, etc.) and a password can be set to prevent changes.

Of course, even if you don't do the above, re-installing isn't a good option for someone who wants to cover his/her tracks, because such a drastic step would certainly raise a few unwanted questions.

---

### Post by jessethouin on 2010-02-05
Good points, all.  As a Linux admin (sorry, I gave up programming a couple years ago), I require root access, so disabling sudo isn't an option.

I did run across this interesting article, though.

[http://linuxgazette.net/139/brownss.html](http://linuxgazette.net/139/brownss.html)

I haven't tried this yet.  Any thoughts from you Linux/C programmers about how easy it would be to bypass all this?  To me, it seems fairly bullet proof.  For small bullets. ;)

---

### Post by McMurdo on 2010-02-05
> **ArrSea said:**
> Yes, this is true. I think that's why it ultimately comes down to a person's heart. If you want to find a way around it, you probably can. That's the whole purpose for accountability; having others in your life who care enough about you to hold you accountable and help you. 

Because honestly, if you really wanted to, you could just pop in a live CD of some Linux distro, and surf away. Anyway, I don't mean to get on a soapbox or anything, and you're welcome to disagree with my position. 

-ArrSea

Actually I agree with you 100%. I was just discussing the technical implications, which *mssever* presented some solutions to that I hadn't thought about.

---

### Post by mssever on 2010-02-07
> **jessethouin said:**
> I did run across this interesting article, though.

[http://linuxgazette.net/139/brownss.html](http://linuxgazette.net/139/brownss.html)

I haven't tried this yet.  Any thoughts from you Linux/C programmers about how easy it would be to bypass all this?  To me, it seems fairly bullet proof.  For small bullets. ;)

Seems like a reasonable approach, though you should bear in mind that recent versions of Ubuntu use Upstart instead of sysvinit, so the details (and practicality) will probably be a bit different.

---

### Post by Mickeyj4j on 2010-02-15
hi i have recently installed openbox on my ubuntu 9.10 os i cant login to gnome/openbox. i can use openboxrc 

i am wondering if my net responsibility is still running inside openbox. i cant find it in teh openbox menu so not sure. 

if you can help i would appreciate it thanks .

---

### Post by mssever on 2010-02-16
> **Mickeyj4j said:**
> hi i have recently installed openbox on my ubuntu 9.10 os i cant login to gnome/openbox. i can use openboxrc 

i am wondering if my net responsibility is still running inside openbox. i cant find it in teh openbox menu so not sure. 

if you can help i would appreciate it thanks .

Net Responsibility is independent of Openbox, Gnome, KDE, or whatever window manage you use. It doesn't even use X. To find out if Net Responsibility is running, use your favorite tool to list the running processes and search for Net Responsibility in that list.

---

### Post by DustStuff on 2010-02-18
First off, a big thanks to those who've invested a lot of time and energy into this project. It is appreciated, and I believe will continue to be appreciated as more people move to Ubuntu or other Linux distros.

One thing I think would be helpful (even at this alpha stage) would be one-stop documentation for Net Responsibility, and I've noticed a similar sentiment in mssever's and other's comments in regards to a forum thread not being the best information repository. Here's what I'm thinking (and am willing to try to get started):

1. Use a post to the Tutorial & Tips area of these forums as a starting point.
2. Go through this thread and include all relevant information.
3. Include a line near the top that mentions 'last revision date', so people can look for newer info in the thread, launchpad, etc.
4. Include links to this page on the first page of this thread (by editing the first post? or by using a sticky post) if possible, as well as on the Net Responsibility website.

In the spirit of the 'Tutorial & Tips' area, I would like this to be something that is accessible to someone not real familiar with Ubuntu/Linux or programming, but could also be useful to those with more experience in these areas. So, I think I would envision the basic document being kept fairly concise, with links to other more detailed documents (possibly hosted on the Net Responsibility website?).

So, that's what I'm thinking. I would do my best to periodically update this proposed page, according to my available time, but have just a few questions to raise for your input:

1. First, is this the best way to go about this?
2. I am a Linux (Ubuntu-based, so far) user, but am not a programmer. Those who are programmers and developers of this program, would you be willing to periodically review a page like this to make sure that the information is still correct, based on current versions, etc.? This is probably especially important for the first draft.

I look forward to hearing from some of you participating in this thread, and hope that I can be of some help in this way, as well as in testing this package as it continues to be developed.

press on,
dust

---

### Post by roggan87 on 2010-02-18
> First off, a big thanks to those who've invested a lot of time and energy into this project. It is appreciated, and I believe will continue to be appreciated as more people move to Ubuntu or other Linux distros.

One thing I think would be helpful (even at this alpha stage) would be one-stop documentation for Net Responsibility, and I've noticed a similar sentiment in mssever's and other's comments in regards to a forum thread not being the best information repository. Here's what I'm thinking (and am willing to try to get started):

1. Use a post to the Tutorial & Tips area of these forums as a starting point.
2. Go through this thread and include all relevant information.
3. Include a line near the top that mentions 'last revision date', so people can look for newer info in the thread, launchpad, etc.
4. Include links to this page on the first page of this thread (by editing the first post? or by using a sticky post) if possible, as well as on the Net Responsibility website.

In the spirit of the 'Tutorial & Tips' area, I would like this to be something that is accessible to someone not real familiar with Ubuntu/Linux or programming, but could also be useful to those with more experience in these areas. So, I think I would envision the basic document being kept fairly concise, with links to other more detailed documents (possibly hosted on the Net Responsibility website?).

So, that's what I'm thinking. I would do my best to periodically update this proposed page, according to my available time, but have just a few questions to raise for your input:

1. First, is this the best way to go about this?
2. I am a Linux (Ubuntu-based, so far) user, but am not a programmer. Those who are programmers and developers of this program, would you be willing to periodically review a page like this to make sure that the information is still correct, based on current versions, etc.? This is probably especially important for the first draft.

I look forward to hearing from some of you participating in this thread, and hope that I can be of some help in this way, as well as in testing this package as it continues to be developed.

press on,
dust 
Hi DustStuff!
I've sent you a private message with some more details.

For everyone else: We're working on making this happen on [www.netresponsibility.com](www.netresponsibility.com), but are still in progress. Please hang in there.

Roggan

---

### Post by roggan87 on 2010-02-23
Release announcement!

We've released a new alpha version on the website, called 2.0a1. Download it here: 
[http://www.netresponsibility.com/download.php]("http://www.netresponsibility.com/download.php")

Changes from 2.0a:
It seems like the automatic reporting is now working as supposed! The only bug here, is that it also sends a new report every new month.
You can now run the command ```
sudo net-responsibility-report --latestreports [optional number]
``` to see a list of the latest successful reports.
The daemon shouldn't stop at manual reports, and if it does, it's also started again. (Maybe not 100% fireproof, but much better and reliable.)

Maybe some other small fixes. 

Feel free to check it out!

Have a good day, and please report any found bugs in this release.

---

### Post by roggan87 on 2010-03-04
If you log in at netresponsibility.com, and look at your configuration, there is now an ability to add/edit your own blacklist and whitelist. You can try it out if you want to, and let me know whether it's working for you or not.

That's all for now.
Roggan

---

### Post by Mickeyj4j on 2010-03-12
puppy linux has any one managed to install and run net responsibility on puppy linux.

i have tryed this on puppy 4.3.1. i also installed ruby as a dependance. 

still i cant run it 
 any ideas would be great 
i have used .deb packages for net responsabiliby and ruby as puppy can install from the easily

---

### Post by Mickeyj4j on 2010-03-13
one thing i find is that net responsibility is to memory hogging my computer runs to slow with it 
it needs to be stripped out so it runs better for some of us on older computers.

CPU:       Single core Intel Pentium 4 (UP) cache 512 KB flags (sse2) clocked at 1835.906 MHz 

System:    Host meowbuntu-desktop Kernel 2.6.31-20-generic i686 (32 bit) Distro Ubuntu 9.10 karmic


this is why my computer runs slow
net responsability needs to be stripped out in my opinion.  

if i disable ruby will net responsability still work

---

### Post by Mickeyj4j on 2010-03-13
although the origional poster of this forum no longer maintains netresponsability this is still the only forum for it.  the new net responsability team have not set up anything else that i can see from there site.

---

### Post by tetralectic on 2010-03-14
> **Mickeyj4j said:**
> one thing i find is that net responsibility is to memory hogging my computer runs to slow with it 
it needs to be stripped out so it runs better for some of us on older computers.

CPU:       Single core Intel Pentium 4 (UP) cache 512 KB flags (sse2) clocked at 1835.906 MHz 

System:    Host meowbuntu-desktop Kernel 2.6.31-20-generic i686 (32 bit) Distro Ubuntu 9.10 karmic


this is why my computer runs slow
net responsability needs to be stripped out in my opinion.  

if i disable ruby will net responsability still workHi Mickeyj4j

I have an old Dell Latitude D630 with a single core Intel Pentium 4, and I find that the Net Responsibility daemon take up 126 MiB (Ubuntu 9.04 32-bit). How does this compare with what you are finding? I find little performance impact on my old machine. I'm not a dev. on this project, but I would imagine that disabling ruby would disasble the daemon.

---

### Post by tetralectic on 2010-03-14
> **Mickeyj4j said:**
> although the origional poster of this forum no longer maintains netresponsability this is still the only forum for it.  the new net responsability team have not set up anything else that i can see from there site.Hi Mickeyj4j

This is still the active forum for this project. Regarding bug reporting, the Net Responsibility Launchpad page is set up to handle that.

---

### Post by mssever on 2010-03-15
> **Mickeyj4j said:**
> CPU:       Single core Intel Pentium 4 (UP) cache 512 KB flags (sse2) clocked at 1835.906 MHz 

System:    Host meowbuntu-desktop Kernel 2.6.31-20-generic i686 (32 bit) Distro Ubuntu 9.10 karmic


this is why my computer runs slow
net responsability needs to be stripped out in my opinion.  

if i disable ruby will net responsability still work

Ruby is the program that runs Net Responsibility. It is required in order for Net Responsibility to work. The memory usage reported for Ruby is actually what Net Responsibility is using. If you can provide some more details (how much memory is being used, how much data is being logged, etc.), it might be helpful. 

(Possible info for the devs:) Even though others have taken over this project, I remember having memory problems in the beginning which were caused by many string concatenations instead of pushing multiple strings onto an array and joining the array once. Ruby's strings are immutable, so you pay a penalty every time you change a string. I don't know how you've changed the code, so this might be irrelevant, but this is one possible cause for high memory usage.

---

### Post by Mickeyj4j on 2010-03-15
> **mssever said:**
> Ruby is the program that runs Net Responsibility. It is required in order for Net Responsibility to work. The memory usage reported for Ruby is actually what Net Responsibility is using. If you can provide some more details (how much memory is being used, how much data is being logged, etc.), it might be helpful.
i have provided what i know 75-100% cpu usage 

> **mssever said:**
> (Possible info for the devs:) Even though others have taken over this project, I remember having memory problems in the beginning which were caused by many string concatenations instead of pushing multiple strings onto an array and joining the array once. Ruby's strings are immutable, so you pay a penalty every time you change a string 

interesting what the fix 

> **mssever said:**
> I don't know how you've changed the code, so this might be irrelevant, but this is one possible cause for high memory usage.
I would not know how to change the code. i let it run as is. so nothing different than what is reporting. I have given how much memory it is using and thats alli know 75-100% of my cpu is in use with ruby. 

others i talked to in #ubuntu and #linux on freenode irc network have said that ruby is a memory hogger.  other applications that do similar like squid do not use ruby and easily do the job without overusing the cpu. squid has to be set up and that takes a while to do. but it run better than this ruby application net responsability.

---

### Post by Mickeyj4j on 2010-03-15
> **tetralectic said:**
> This is still the active forum for this project. Regarding bug reporting, the Net Responsibility Launchpad page is set up to handle that.

How do i do that

---

### Post by tetralectic on 2010-03-15
> **Mickeyj4j said:**
> How do i do thatHi Mickeyj4j

Go to [https://launchpad.net/netresponsibility](https://launchpad.net/netresponsibility) and click in the link that says "[COLOR=Red]Report a Bug[/COLOR]".

[QUOTE=Mickeyj4j]i have provided what i know 75-100% cpu usage[/QUOTE]

Net Responsibility 2.0 will run a high CPU when it's analyzing the logs prior to sending a report. The time it runs a high CPU depends on the size of the log file (which depends on the amount of web surfing done and the report interval (I set my report interval to daily to keep this analysis time down and provide smaller reports to my accountability partners)). I typically find that it runs a high CPU for 5-15 minutes. If it's running a high CPU all the time then something is indeed wrong (if you have a long report interval and do a lot of web surfing, then the high CPU analysis prior to sending out a report can take a long time to complete). What happens when you type "sudo net-responsibility-report --testmail" at the command line?

---

### Post by Mickeyj4j on 2010-03-18
I also wish to mention that when i run this command $ sudo killall ruby. my cpu goes down to 11-50 % straight away. 


> **tetralectic said:**
> 
What happens when you type "sudo net-responsibility-report --testmail" at the command line?

this is output 

$ sudo net-responsibility-report --testmail
Downloading the configurationfile...
Loading it.
Downloading blacklist for Porn
Downloading blacklist for Pornstars
Downloading blacklist for Models
Downloading blacklist for Celebrities
Downloading blacklist for Pornstars_extended
net-responsibility-report[4453]: Generating report
net-responsibility-report[4453]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[4453]: /usr/lib/ruby/1.8/sqlite3/errors.rb:62:in 'check': unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[4453]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:121:in 'close'
net-responsibility-report[4453]: => from /usr/local/bin/net-responsibility-report:113:in 'initialize'
net-responsibility-report[4453]: => from /usr/local/bin/net-responsibility-report:131:in 'new'
net-responsibility-report[4453]: => from /usr/local/bin/net-responsibility-report:131
net-responsibility-report[4453]: Time for this report: 11.451088
/usr/lib/ruby/1.8/sqlite3/errors.rb:62:in `check': database is locked (SQLite3::BusyException)
	from /usr/lib/ruby/1.8/sqlite3/resultset.rb:56:in `check'
	from /usr/lib/ruby/1.8/sqlite3/resultset.rb:48:in `commence'
	from /usr/lib/ruby/1.8/sqlite3/resultset.rb:38:in `initialize'
	from /usr/lib/ruby/1.8/sqlite3/statement.rb:135:in `new'
	from /usr/lib/ruby/1.8/sqlite3/statement.rb:135:in `execute'
	from /usr/lib/ruby/1.8/sqlite3/database.rb:245:in `query'
	from /usr/share/net-responsibility/lib/modules/db.rb:101:in `log_report_start'
	from /usr/local/bin/net-responsibility-report:93:in `initialize'
	from /usr/local/bin/net-responsibility-report:131:in `new'
	from /usr/local/bin/net-responsibility-report:131

---

### Post by henjj on 2010-04-09
Thanks for the great accountability software.  

I have two questions.  

First, is there a way to specify what *time* a daily report gets sent out? 

Second, is there a way to send out more than one report a day?  

For instance, if I wanted to automatically send a report out at 10 am in the morning and then another one out at 3pm in the afternoon, would there be a way to do this using net responsibility?

Thanks,

---

### Post by roggan87 on 2010-04-13
> **henjj said:**
> Thanks for the great accountability software.  

I have two questions.  

First, is there a way to specify what *time* a daily report gets sent out? 

Second, is there a way to send out more than one report a day?  

For instance, if I wanted to automatically send a report out at 10 am in the morning and then another one out at 3pm in the afternoon, would there be a way to do this using net responsibility?

Thanks,

Hi!

Thanks for using it :)

You can't achieve what you want to in the Net Responsibility settings. But in Linux there are always a bunch of ways to do things ;) I'd suggest you take a look at cron ([https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)), to set up scheduled reports. To send manual reports, you use the command
```
sudo net-responsibility-report
```
Make sure you have root privileges when you're setting up cron.

I'd set the report frequency to a pretty high number, so it doesn't send out reports when you're not expecting it to, if you haven't had internet access for some days.

I haven't tried this myself, so please correct me if I'm wrong, anyone.

Good luck!
Roggan

---

### Post by xtemplarx on 2010-05-03
Does anybody know if the same Net-Responsibility username and pword can work for two separate systems running the software simultaneously, or will that cause problems?  Does each need its own username/pword?

I'm only asking because in my scenario, there's the desktop and a laptop.  Desktop sees more use, but want the daemon running to monitor both.

---

### Post by tetralectic on 2010-05-03
> **xtemplarx said:**
> Does anybody know if the same Net-Responsibility username and pword can work for two separate systems running the software simultaneously, or will that cause problems?  Does each need its own username/pword?

I'm only asking because in my scenario, there's the desktop and a laptop.  Desktop sees more use, but want the daemon running to monitor both.
Hi xtemplarx

I asked the roggan87 (current dev) about this and he said that each machine needs a different account. The "same Net-Responsibility username and pword" would point to the same Net Responsibility account from both machines, and won't work. This being so, I have two accounts (one for my desktop and one for my laptop) with different usernames. However I have the same password for both accounts. Having two accounts means that two separate reports are sent out.

---

### Post by xtemplarx on 2010-05-03
> **tetralectic said:**
> Hi xtemplarx

I asked the roggan87 (current dev) about this and he said that each machine needs a different account. The "same Net-Responsibility username and pword" would point to the same Net Responsibility account from both machines, and won't work. This being so, I have two accounts (one for my desktop and one for my laptop) with different usernames. However I have the same password for both accounts. Having two accounts means that two separate reports are sent out.

Thanks much!  I was hoping the solution would be simple, as it didn't appear to be working properly as it was.  :)

---

### Post by roggan87 on 2010-05-04
> I asked the roggan87 (current dev) about this and he said that each machine needs a different account. The "same Net-Responsibility username and pword" would point to the same Net Responsibility account from both machines, and won't work. This being so, I have two accounts (one for my desktop and one for my laptop) with different usernames. However I have the same password for both accounts. Having two accounts means that two separate reports are sent out. 

Hi there!
I'm sorry if I've said that. You are actually able to use the same account for two different computers. I'm using my account for both a desktop and a laptop.

BUT, that means you will also use the same settings for both computers, so you cannot use the same account if you want different frequencies of the reports etc.

AND, both computers will send out reports independent of each other. (I think that was what I meant when speaking to tetralectic) So if you've set up Net Responsibility to send one report a week, and use it on two computers, your accountability partners will end up having two reports a week, without knowing which one is from which computer.

If anyone have experienced troubles with having the same account for two computers, please report at LaunchPad.

Hope that clarifies some misunderstandings.

Blessings!
Roggan

---

### Post by xtemplarx on 2010-05-04
> **roggan87 said:**
> Hi there!
I'm sorry if I've said that. You are actually able to use the same account for two different computers. I'm using my account for both a desktop and a laptop.

BUT, that means you will also use the same settings for both computers, so you cannot use the same account if you want different frequencies of the reports etc.

AND, both computers will send out reports independent of each other. (I think that was what I meant when speaking to tetralectic) So if you've set up Net Responsibility to send one report a week, and use it on two computers, your accountability partners will end up having two reports a week, without knowing which one is from which computer.

If anyone have experienced troubles with having the same account for two computers, please report at LaunchPad.

Hope that clarifies some misunderstandings.

Blessings!
Roggan

Thanks, Roggan!

---

### Post by tetralectic on 2010-05-04
> **roggan87 said:**
> Hi there!
I'm sorry if I've said that. You are actually able to use the same account for two different computers. I'm using my account for both a desktop and a laptop.

BUT, that means you will also use the same settings for both computers, so you cannot use the same account if you want different frequencies of the reports etc.

AND, both computers will send out reports independent of each other. (I think that was what I meant when speaking to tetralectic) So if you've set up Net Responsibility to send one report a week, and use it on two computers, your accountability partners will end up having two reports a week, without knowing which one is from which computer.

If anyone have experienced troubles with having the same account for two computers, please report at LaunchPad.

Hope that clarifies some misunderstandings.

Blessings!
Roggan

Hi Roggan

Thanks for the clarification, I'll try it out. I likely misheard and/or misunderstood what you said :o

tetralectic

---

### Post by Dave_KC on 2010-05-09
Hi everyone:

I'm having trouble getting my Net-Responsibility to work.  It's version 0.5.0.  Here's the error report when I try to send a report manually.  

> sudo net-responsibility-report
[sudo] password for david: 
net-responsibility-report[5910]: Generating report
net-responsibility-report[5910]: Sending report
send: 'ehlo [127.0.1.1]\r\n'
reply: '250-lavabit.com\r\n'
reply: '250-8BITMIME\r\n'
reply: '250-STARTTLS\r\n'
reply: '250-PIPELINING\r\n'
reply: '250-SIZE 1073741824\r\n'
reply: '250-AUTH LOGIN PLAIN\r\n'
reply: '250-AUTH=LOGIN PLAIN\r\n'
reply: '250 Okay.\r\n'
reply: retcode (250); Msg: lavabit.com
8BITMIME
STARTTLS
PIPELINING
SIZE 1073741824
AUTH LOGIN PLAIN
AUTH=LOGIN PLAIN
Okay.
send: 'mail FROM:<chieffan@lavabit.com> size=58708619\r\n'
reply: '250 Sender okay.\r\n'
reply: retcode (250); Msg: Sender okay.
send: 'rcpt TO:<iampierre@gmail.com>\r\n'
reply: '554 Recipient is not recognized. Relay access denied.\r\n'
reply: retcode (554); Msg: Recipient is not recognized. Relay access denied.
send: 'rcpt TO:<john.glisson@gmail.com>\r\n'
reply: '554 Recipient is not recognized. Relay access denied.\r\n'
reply: retcode (554); Msg: Recipient is not recognized. Relay access denied.
send: 'rcpt TO:<chitato33@hotmail.com>\r\n'
reply: '554 Recipient is not recognized. Relay access denied.\r\n'
reply: retcode (554); Msg: Recipient is not recognized. Relay access denied.
send: 'rcpt TO:<chieffan@lavabit.com>\r\n'
reply: '550 The IP address 65.31.221.90 has been listed on a realtime blacklist, and the user [email]chieffan@lavabit.com[/email] has elected to enforce blacklists.\r\n'
reply: retcode (550); Msg: The IP address 65.31.221.90 has been listed on a realtime blacklist, and the user [email]chieffan@lavabit.com[/email] has elected to enforce blacklists.
send: 'rcpt TO:<dpcapp@gmail.com>\r\n'
reply: '554 Recipient is not recognized. Relay access denied.\r\n'
reply: retcode (554); Msg: Recipient is not recognized. Relay access denied.
send: 'rset\r\n'
reply: '250 Okay.\r\n'
reply: retcode (250); Msg: Okay.
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 96, in <module>
    result = s.sendmail(config['email_from'],toaddrs,msg)
  File "/usr/lib/python2.6/smtplib.py", line 709, in sendmail
    raise SMTPRecipientsRefused(senderrs)
smtplib.SMTPRecipientsRefused: {'iampierre@gmail.com': (554, 'Recipient is not recognized. Relay access denied.'), 'chieffan@lavabit.com': (550, 'The IP address 65.31.221.90 has been listed on a realtime blacklist, and the user [email]chieffan@lavabit.com[/email] has elected to enforce blacklists.'), 'dpcapp@gmail.com': (554, 'Recipient is not recognized. Relay access denied.'), 'john.glisson@gmail.com': (554, 'Recipient is not recognized. Relay access denied.'), 'chitato33@hotmail.com': (554, 'Recipient is not recognized. Relay access denied.')}
net-responsibility-report[5910]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[5910]: /usr/lib/ruby/1.8/sqlite3/errors.rb:62:in 'check': unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[5910]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:121:in 'close'
net-responsibility-report[5910]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[5910]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[5910]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/report_mailer.rb:86:in `send_message': send-report.py exited due to an unhandled exception. (RuntimeError)
	from /usr/share/net-responsibility/lib/report_mailer.rb:96:in `create_and_send'
	from /usr/local/bin/net-responsibility-report:89:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119


I'd appreciate help in figuring it out.  

Dave

---

### Post by roggan87 on 2010-05-10
> I'm having trouble getting my Net-Responsibility to work. It's version 0.5.0.

Hi Dave!

It might be your settings, email server, or recipients that's causing this error. I'd strongly suggest you install version 2.0a1 for better reports and easier setup.

Good luck :)

---

### Post by Dave_KC on 2010-05-10
> **roggan87 said:**
> Hi Dave!

It might be your settings, email server, or recipients that's causing this error. I'd strongly suggest you install version 2.0a1 for better reports and easier setup.

Good luck :)

I've loaded the newer version, only to have it crash instantly when trying to load the configuration utility.  I'm using a 64 bit OS too.  (Mint).

---

### Post by Dave_KC on 2010-05-10
> **Dave_KC said:**
> I've loaded the newer version, only to have it crash instantly when trying to load the configuration utility.  I'm using a 64 bit OS too.  (Mint).

Out of frustration I installed the new one, and I think I might know what happened, and might be better now.  The configuration utility actually works now.

---

### Post by zalutz on 2010-05-10
Absolute noob

Very new to ubuntu 10.04 64 bit. I was just trying to figure out how to get this to work correctly. If this question has already been answered let me know, I'm just in over my head with the ubuntu forums. I've gone through the "walk-thru" on net responsibility's website twice now and don't really know where to head next. Thanks for your help.

The following is my output from *sudo net-responsibility-report*

```
net-responsibility-report[27474]: Generating report
net-responsibility-report[27474]: Sending report
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 78, in <module>
    except (smtplib.SMTPException,smtplib.socket.error,socket.error), e:
NameError: name 'socket' is not defined
net-responsibility-report[27474]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[27474]: /usr/lib/ruby/1.8/sqlite3/errors.rb:62:in 'check': unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[27474]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:121:in 'close'
net-responsibility-report[27474]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[27474]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[27474]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/report_mailer.rb:86:in `send_message': send-report.py exited due to an unhandled exception. (RuntimeError)
	from /usr/share/net-responsibility/lib/report_mailer.rb:96:in `create_and_send'
	from /usr/local/bin/net-responsibility-report:89:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119
zalutz@zalutz-laptop:~$ 

```

---

### Post by oleink on 2010-06-03
How do you understand the reports being sent by net responsibility.  I can't tell which sites they visited etc.

---

### Post by oleink on 2010-06-03
> **zalutz said:**
> Absolute noob

Very new to ubuntu 10.04 64 bit. I was just trying to figure out how to get this to work correctly. If this question has already been answered let me know, I'm just in over my head with the ubuntu forums. I've gone through the "walk-thru" on net responsibility's website twice now and don't really know where to head next. Thanks for your help.

The following is my output from *sudo net-responsibility-report*

```
net-responsibility-report[27474]: Generating report
net-responsibility-report[27474]: Sending report
Traceback (most recent call last):
  File "/usr/share/net-responsibility/lib/send_report.py", line 78, in <module>
    except (smtplib.SMTPException,smtplib.socket.error,socket.error), e:
NameError: name 'socket' is not defined
net-responsibility-report[27474]: The following exception (SQLite3::BusyException) is caused by a known bug. If you know how to fix it, do tell! Otherwise, you can safely ignore it (I hope).
net-responsibility-report[27474]: /usr/lib/ruby/1.8/sqlite3/errors.rb:62:in 'check': unable to close due to unfinalised statements (SQLite3::BusyException)
net-responsibility-report[27474]: => from /usr/lib/ruby/1.8/sqlite3/database.rb:121:in 'close'
net-responsibility-report[27474]: => from /usr/local/bin/net-responsibility-report:103:in 'initialize'
net-responsibility-report[27474]: => from /usr/local/bin/net-responsibility-report:119:in 'new'
net-responsibility-report[27474]: => from /usr/local/bin/net-responsibility-report:119
/usr/share/net-responsibility/lib/report_mailer.rb:86:in `send_message': send-report.py exited due to an unhandled exception. (RuntimeError)
	from /usr/share/net-responsibility/lib/report_mailer.rb:96:in `create_and_send'
	from /usr/local/bin/net-responsibility-report:89:in `initialize'
	from /usr/local/bin/net-responsibility-report:119:in `new'
	from /usr/local/bin/net-responsibility-report:119
zalutz@zalutz-laptop:~$ 

```

It said it is a common bug.  Look it up on their site

---

### Post by oleink on 2010-06-03
How do you understand the reports being sent by net responsibility. I can't tell which sites they visited etc.

---

### Post by tetralectic on 2010-06-03
> **oleink said:**
> How do you understand the reports being sent by net responsibility. I can't tell which sites they visited etc.
Hi oleink

This below is a report for a brief bit of web browsing I did in a short interval of time.> 
**Shutdowns**

 The program hasn't been interrupted.**Warnings**

 
No  matches found (which is good)**Whitelist**

 No matches with  blacklist *and* whitelist**All hostnames**

 
**2010-06-03:  (Total: 25)**

 
[ads.ad4game.com]("http://ads.ad4game.com/"),  [api.wunderground.com]("http://api.wunderground.com/"),  [disqus.com]("http://disqus.com/"), [event.adxpose.com]("http://event.adxpose.com/"),
     [googleads.g.doubleclick.net]("http://googleads.g.doubleclick.net/"),  [graphics8.nytimes.com]("http://graphics8.nytimes.com/"),  [***************]("http://***************/"), [lh5.ggpht.com]("http://lh5.ggpht.com/"),
    [mirror.toolbar.netcraft.com]("http://mirror.toolbar.netcraft.com/"),  [nht-2.extreme-dm.com]("http://nht-2.extreme-dm.com/"),  [omgubuntu.disqus.com]("http://omgubuntu.disqus.com/"),  [pubads.g.doubleclick.net]("http://pubads.g.doubleclick.net/"),
     [timespeople.nytimes.com]("http://timespeople.nytimes.com/"),  [up.nytimes.com]("http://up.nytimes.com/"), [www.apture.com]("http://www.apture.com/"), [www.blogger.com]("http://www.blogger.com/"),
     [www.google-analytics.com]("http://www.google-analytics.com/"),  [www.google.com]("http://www.google.com/"), [www.megaupload.com]("http://www.megaupload.com/"),  [www.netresponsibility.com]("http://www.netresponsibility.com/"),
     [www.netupd8.com]("http://www.netupd8.com/"),  [www.nytimes.com]("http://www.nytimes.com/"), [www.webupd8.org]("http://www.webupd8.org/"), [www628.megaupload.com]("http://www628.megaupload.com/"),
     [wwwstatic.megaupload.com]("http://wwwstatic.megaupload.com/")

 **All  visited sites**

 **[ads.ad4game.com]("http://ads.ad4game.com/")**

 
/www/delivery/al.php?zoneid= 3896&layerstyle=footer&position=bottom&speed=3&slide=0&delay=2&ahere=f&transparent=t

**[api.wunderground.com]("http://api.wunderground.com/")**


/auto/wui/geo/ForecastXML/index.xml?query=73019

/auto/wui/geo/WXCurrentObXML/index.xml?query=73019

**[disqus.com]("http://disqus.com/")**


/forums/webupd8/embed.js
/forums/webupd8/recent_comments_widget.js?num_items=7&hide_avatars=0&avatar_size=32&excerpt_length=100


**[event.adxpose.com]("http://event.adxpose.com/")**


/event.flow?eventcode=000_000_4&location=http%3A%2F%[2Fgoogleads.g.doubleclick.net]("http://2fgoogleads.g.doubleclick.net/")%2Fpagead%2Fads%3Fclient%3Dca-pub-5111779714716360%26output%3Dhtml%26h%3D250%26slotname%3D4357447028%26w%3D300%26lmt%3D1275578400%26host%3Dpub-1556223355139109%26h_ch%3D00000%26flash%3D10    .0.45%26url%3Dhttp%253A%252F%[252Fwww.webupd8.org]("http://252fwww.webupd8.org/")%252F2010%252F06%252Fnautilus-elementary-2311-now-with.html%26dt%3D1275592868541%26shv%3Dr20100526%26prev_slotnames%3D5019549445%252C2038158809%26correlator%3D1275592867275%26pv_h_ch%3D00000%26frm%3D0%26adk%3D3433778769%26ga_vid%3D1996309922.1275587592%26ga_sid%3D1275587592%26ga_hid%3D2032264218%26ga_fc%3D1%26u_tz%3D-300%26u_his%3D1%26u_java%3D1%26u_h%3D800%26u_w%3D1280%26u_ah%3D775%26u_aw%3D1218%26u_cd%3D24%26u_nplug%3D15%26u_nmime%3D221%26biw%3D1202%26bih%3D558%26fu%3D0%26ifi%3D3%26dtd%3D3%26xpc%3DgTMTdcJ8xu%26p%3Dhttp%253A%2F%[2Fwww.webupd8.org]("http://2fwww.webupd8.org/")&uid=XHor1zvIXtcRZFG4&xy=0%2C0&wh=300%2C250&duration=4731&iframed=1

**[googleads.g.doubleclick.net]("http://googleads.g.doubleclick.net/")**


/pagead/ads?client=ca-pub-5111779714716360&output=html&h=280&slotname=2038158809&w=336&lmt=1275578400&host=pub-1556223355139109&h_ch=00000&flash=10.0.45&url=http%3A%2F%[2Fwww.webupd8.org]("http://2fwww.webupd8.org/")%2F2010%2F06%2Felementary-icon-theme-for-empathy.html&dt=1275592856396&shv=r20100526&prev    _slotnames=5019549445&correlator=1275592856239&pv_h_ch=00000&frm=0&adk=4090649186&ga_vid=1996309922.1275587592&ga_sid=1275587592&ga_hid=2095444620&ga_fc=1&u_tz=-300&u_his=1&u_java=1&u_h=800&u_w=1280&u_ah=775&u_aw=1218&u_cd=24&u_nplug=15&u_nmime=221&biw=1202&bih=556&fu=0&ifi=2&dtd=4&xpc=y0L0fUaLfX&p=http%3A//[www.webupd8.org]("http://www.webupd8.org/")
/pagead/ads?client=ca-pub-5111779714716360&output=html&h=280&slotname=5019549445&w=336&lmt=1275578400&host=pub-1556223355139109&h_ch=00000&flash=10.0.45&url=http%3A%2F%[2Fwww.webupd8.org]("http://2fwww.webupd8.org/")%2F2010%2F06%2Felementary-icon-theme-for-empathy.html&dt=1275592856237&shv=r20100526&correlator=1275592856239&frm=0&adk=2422522717&ga_vid=1996309922.1275587592&ga_sid=1275587592&ga_hid=2095444620&ga_fc=1&u_tz=-300&u_his=1&u_java=1&u_h=800&u_w=1280&u_ah=775&u_aw=1218&u_cd=24&u_nplug=15&u_nmime=221&biw=1218&bih=556&fu=0&ifi=1&dtd=122&xpc=hLweQ8LJoL&p=http%3A//[www.webupd8.org]("http://www.webupd8.org/")

**[graphics8.nytimes.com]("http://graphics8.nytimes.com/")**


/css/0.1/print/styles.css

/images/2010/06/04/business/04    shop1/04shop1-articleInline.jpg
/images/2010/06/04/business/20100604_WEBSHOP_graphics/20100604_WEBSHOP_graphics-popup-v3.jpg
/images/2010/06/04/business/20100604_WEBSHOP_graphics/20100604_WEBSHOP_graphics-thumbWide-v3.jpg
/images/multimedia/closewindow.gif
/js/app/analytics/trackingTags_v1.1.js

/js2/build/homepage/top.js


**[***************]("http://***************/")**


/_FJH0hYZmVtc/TAeoyKFUM_I/AAAAAAAAIGU/9Qkk6GvvCqo/image%5B3%5D.png?imgmax=800

**[lh5.ggpht.com]("http://lh5.ggpht.com/")**


/_FJH0hYZmVtc/TAfEIFs5XtI/AAAAAAAAIGs/HZ8Ej8b4x0U/MaverickMeerkatWallThree%20%281%29_thumb%5B1%5D.png?imgmax=800

**[mirror.toolbar.netcraft.com]("http://mirror.toolbar.netcraft.com/")**


/check_url/[http://www.nytimes.com/3354364104](http://www.nytimes.com/3354364104)

**[nht-2.extreme-dm.com]("http://nht-2.extreme-dm.com/")**


/n2.g?login=kimble&pid=main&jv=y&j=y&srw=1280&srb=24&l=

**[omgubuntu.disqus.com]("http://omgubuntu.disqus.com/")**


/timer.html?nonce=-:2010-06-03T13:34:41.231618&thread_id=102877041

**[pubads.g.doubleclick.net]("http://pubads.g.doubleclick.net/")**


/gampad/ads?correlator=1275592904044&output=json_html&c    allback=GA_googleSetAdContentsBySlotForSync&impl=s&eid=31865001&client=ca-pub-1150932386931372&slotname=fullsizebanner&page_slots=fullsizebanner&cookie=ID%3Db5c764f95480aa00%3AT%3D1275592891%3AS%3DALNI_MZGXRt2pz_1Gmi5_bciM55TjwS4CQ&ga_vid=1508598911.1275592904&ga_sid=1275592904&ga_hid=1485063081&url=http%3A%2F%2Fgnome-look.org%2Fcontent%2Fdownload.php%3Fcontent%3D125657%26id%3D1%26tan%3D20918414%26PHPSESSID%3Ddc0fd791e99e3462649b968c0806198f&lmt=1275592903&dt=1275592904063&cc=100&biw=1218&bih=556&ifi=1&adk=43235900&u_tz=-300&u_his=2&u_java=true&u_h=800&u_w=1280&u_ah=775&u_aw=1218&u_cd=24&u_nplug=15&u_nmime=221&flash=10.0.45

**[timespeople.nytimes.com]("http://timespeople.nytimes.com/")**


/packages/html/timespeople/xmlhttprequest.html?url=%2Fsvc%2Ftimespeople%2Ftoolbar%2F1.0%2Fuser%3Fpage_url%3Dhttp%3A%2F%[2Fwww.nytimes.com]("http://2fwww.nytimes.com/")%2F2010%2F06%2F04%2Fbusiness%2Feconomy%2F04shop.html%3Fhpw&method=get&params=&bell=[http://www.nytimes.com/svc/timespeople/bell.html](http://www.nytimes.com/svc/timespeople/bell.html)
/svc/timespeople/toolbar/1.0/user?page_url=    [http://www.nytimes.com/2010/06/04/business/economy/04shop.html?hpw](http://www.nytimes.com/2010/06/04/business/economy/04shop.html?hpw)

**[up.nytimes.com]("http://up.nytimes.com/")**


/?d=0//&t=10&s=0&ui=0&r=&u=www%2enytimes%2ecom%2fimagepages%2f2010%2f06%2f04%2fbusiness%2f20100604%5fWEBSHOP%5fgraphics%2ehtml%3fref%3deconomy
/?d=0/4/&t=2&s=0&ui=0&r=&u=www%2enytimes%2ecom%2f2010%2f06%2f04%2fbusiness%2feconomy%2f04shop%2ehtml%3fhpw%3d

**[www.apture.com]("http://www.apture.com/")**


/t/v2/?2=%7B%22pageId%22%3A60414375%2C%22visitId%22%3A145061524336655%2C%22duration%22%3A6357958%2C%22numLinks%22%3A0%2C%22numLinksOpened%22%3A0%2C%22durationPopupsOpened%22%3A0%2C%22referrer%22%3A%22%22%2C%22numTmmLinks%22%3A0%2C%22type%22%3A25%2C%22siteId%22%3A129675%7D

**[www.blogger.com]("http://www.blogger.com/")**


/dyn-css/authorization.css?targetBlogID=7452102844869359296&zx=1b93ba77-23a2-4f60-a795-cf2dd2aae834

/navbar.g?targetBlogID=7452102844869359296&blogName=Web+Upd8&publishMode=PUBLISH_MODE_HOSTED&navbarType=BLUE&layoutType=LAYOUTS&searchRoot=http%3A%2F%[2Fwww.webupd8.org]("http://2fwww.webupd8.org/")%2Fsearch&blogLocale    =en&homepageUrl=http%3A%2F%[2Fwww.webupd8.org]("http://2fwww.webupd8.org/")%2F&targetPostID=6679949108014639672

**[www.google-analytics.com]("http://www.google-analytics.com/")**


/__utm.gif?utmwv=4.7.2&utmn=2046832162&utmhn=[www.webupd8.org]("http://www.webupd8.org/")&utmcs=UTF-8&utmsr=1280x800&utmsc=24-bit&utmul=en-us&utmje=1&utmfl=10.0%20r45&utmdt=Elementary%20Icon%20Theme%20For%20Empathy%20Updated%20(Elementary%20Empathy%202)%20~%20Web%20Upd8&utmhid=2095444620&utmr=-&utmp=%2F2010%2F06%2Felementary-icon-theme-for-empathy.html&utmac=UA-7585273-1&utmcc=__utma%3D6323892.1996309922.1275587592.1275587592.1275587592.1%3B%2B__utmz%3D6323892.1275587592.1.1.utmcsr%3D(direct)%7Cutmccn%3D(direct)%7Cutmcmd%3D(none)%3B&gaq=1

**[www.google.com]("http://www.google.com/")**


/buzz/api/button.js
/buzz/api/buzzThis/buzzCounter?url=http%3A%2F%[2Fwww.webupd8.org]("http://2fwww.webupd8.org/")%2F2010%2F06%2Felementary-icon-theme-for-empathy.html

**[www.megaupload.com]("http://www.megaupload.com/")**


/?d=WFVFQVL6

**[www.netresponsibility.com]("http://www.netresponsibility.com/")**


/config.php


**[www.netupd8.com]("http://www.netupd8.com/")**


/webupd8/fonts/fonts/bpreplay.t  tf

**[www.nytimes.com]("http://www.nytimes.com/")**


/2010/06/04/business/economy/04shop.html?hpw
/adx/bin/adx_remote.html?type=fastscript&page=[www.nytimes.com/yr/mo/day/&posall=Frame6A&query=qstring&keywords=]("http://www.nytimes.com/yr/mo/day/&posall=Frame6A&query=qstring&keywords=")?
/svc/timespeople/bell.html


**[www.webupd8.org]("http://www.webupd8.org/")**


/2010/06/elementary-icon-theme-for-empathy.html
/feeds/posts/default/-/elementary?alt=json-in-script&callback=listEntries10

**[www628.megaupload.com]("http://www628.megaupload.com/")**


/files/f60a04a9cf0740ca198dfae91e7da725/lucid-splash-image.deb

**[wwwstatic.megaupload.com]("http://wwwstatic.megaupload.com/")**


/gui2/dnld_tabbie.gif
/gui2/en/but_dnld_premium.gif
/gui2/en/but_dnld_premium_o.gif
/gui2/en/but_dnld_regular.gif
/gui2/en/but_dnld_regular_o.gif
/gui2/en/dnld_table.gif
/gui2/n.gif
/gui2/y.gif
 
 It says under Shutdowns that I didn't interupt the daemon. There were no Warnings, i.e. no web sites that matched the lists that I am using (configured on the web site). Also under Whitelists, no web sites that these lists would flag that are in fact okay (again configured on the web site). Then there's All the host names that this computer contacted. I visited>  [www.google.com]("http://www.google.com/"), [www.megaupload.com]("http://www.megaupload.com/"),  [www.netresponsibility.com]("http://www.netresponsibility.com/"),
     [www.netupd8.com]("http://www.netupd8.com/"),  [www.nytimes.com]("http://www.nytimes.com/"), [www.webupd8.org]("http://www.webupd8.org/"),. The rest are the domain names that these websites themselves pulled in. Then, beneath that, under All Visited Sites, are the details.

---

### Post by oleink on 2010-06-03
> **tetralectic said:**
> Hi oleink

This below is a report for a brief bit of web browsing I did in a short interval of time. It says under Shutdowns that I didn't interupt the daemon. There were no Warnings, i.e. no web sites that matched the lists that I am using (configured on the web site). Also under Whitelists, no web sites that these lists would flag that are in fact okay (again configured on the web site). Then there's All the host names that this computer contacted. I visited. The rest are the domain names that these websites themselves pulled in. Then, beneath that, under All Visited Sites, are the details.

Ok that is what I figured.  I just could not get the websites to visit the "paths" for some reason (like put the website then the path name.) Another thing is that mine did not list whether or not they visited any sites with the lists.  Like it didn't say there were any warnings or that there weren't.  It didn't say anything except for whether it was shut down or not....???

---

### Post by JSuresh on 2010-06-21
The new Net Responsibility looks great so far.  

One question: I'm a big fan of Google Chrome now.. does it track both normal and incognito modes of Google Chrome?  Thanks

---

### Post by mssever on 2010-06-22
> **JSuresh said:**
> The new Net Responsibility looks great so far.  

One question: I'm a big fan of Google Chrome now.. does it track both normal and incognito modes of Google Chrome?  Thanks
Unless it's been changed recently, it should monitor all HTTP traffic on your computer, regardless of which browser/browser mode/browser settings you use. In fact, even if another program makes an automated connection over HTTP, that should be logged, too.

---

### Post by mpnordland on 2010-06-26
can i configure it for different users on one computer? eg each user has it's own net responsibility account

---

### Post by roggan87 on 2010-06-28
> 
[QUOTE]The new Net Responsibility looks great so far.

One question: I'm a big fan of Google Chrome now.. does it track both normal and incognito modes of Google Chrome? Thanks

Unless it's been changed recently, it should monitor all HTTP traffic on your computer, regardless of which browser/browser mode/browser settings you use. In fact, even if another program makes an automated connection over HTTP, that should be logged, too. [/QUOTE]

Hi!
Just confirming that it hasn't been changed. Net Responsibility will log all HTTP traffic, including incognito mode in Google Chrome, and Private surfing in Firefox etc.

> can i configure it for different users on one computer? eg each user has it's own net responsibility account 

Currently it's impossible (as far as I know, unless there is some clever Linux solution), but it's a feature that might be included in the future.

I can also say that a new version is on it's way with some very interesting features, that will make the reports easier to read by the accountability partners. It should be available in a couple of weeks.

Take care!

---

### Post by mpnordland on 2010-06-28
I am willing to try and develop it, if i can help by using python, i looked at ruby, and the net-responsibility source and i was sooo confused, but I am fairly proficient with python, and i had the following ideas as to how multi users should work:
user specific config file in .net-responsibility folder in that users home directory
user specific url log in above mentioned dir,
on any user log in/out /switch event, get the user name and start recording url logs to that users home dir
This needs to get done before my family can complete the switch to linux/ubuntu on our main computer, so if you can, please place it high on the list of things to add, and please tell me if i can help. thanks
micah

---

### Post by mssever on 2010-06-29
> **mpnordland said:**
> I am willing to try and develop it, if i can help by using python, i looked at ruby, and the net-responsibility source and i was sooo confused, but I am fairly proficient with python, and i had the following ideas as to how multi users should work:
user specific config file in .net-responsibility folder in that users home directory
user specific url log in above mentioned dir,
on any user log in/out /switch event, get the user name and start recording url logs to that users home dir
This needs to get done before my family can complete the switch to linux/ubuntu on our main computer, so if you can, please place it high on the list of things to add, and please tell me if i can help. thanks
micah
How do you propose to handle the case where multiple users are logged in simultaneously?

To my knowledge, it's not possible to find out which user is responsible for a particular request, though that data would be incredibly useful. There must be a way, but it may well involve delving into the kernel itself.

---

### Post by Nicodemus144 on 2010-07-07
thanks for making this, guys!  it's a Godsend.

questions: 

1) do i have to uninstall the old version before installing the new one?  and if so, what's the best way to completely do this?

2) any plans for more up-to-date 64-bit versions? my 64-bit box is currently stuck with .5. =)

thanks and keep up the great work!  i look forward to the next release!

---

### Post by tetralectic on 2010-07-08
> **Nicodemus144 said:**
> thanks for making this, guys!  it's a Godsend.

questions: 

1) do i have to uninstall the old version before installing the new one?  and if so, what's the best way to completely do this?

2) any plans for more up-to-date 64-bit versions? my 64-bit box is currently stuck with .5. =)

thanks and keep up the great work!  i look forward to the next release!

Hi Nicodemus144

It's not hard to make a 2.0a1 64-bit .deb package from the source code (.tar.gz file), and then install it using the GDebi package installer. Have a look at "**Installation Instructions"** on the Net Responsibility website, and follow the ReadMe file in the source package. It's important though to follow the work around to **"6. Installing from source on a 64-bit machine fails**" under "**Known bugs**", also on the Net Responsibility website.

When installing a new version of Net Responsibility I always completely uninstall the earlier version. I have fewer problems that way.

roggan87's last post mentions that a new and improved version of 2.0 will be released in a week or so and I'm looking forward to this. I also find Net Responsibility a a Godsend.

:P

---

### Post by mssever on 2010-07-08
> **tetralectic said:**
> When installing a new version of Net Responsibility I always completely uninstall the earlier version. I have fewer problems that way.
If that's the case, then it's a bug. The way APT works, you should always be able to upgrade from version to version without problems (since this upgrade doesn't involve critical system libraries, kernels, or other complicated stuff). If you have to uninstall first, then there's a bug in the packaging.

---

### Post by semijoyful on 2010-07-18
Hi, all!  I am building this thing for my 64 bit system, and I am stuck on part of the installation instructions.  I get that I need to make all those directories and move files over.  I am confused when the letters change up.  This is what I am talking about:

```
c 0600 root root /etc/net-responsibility.conf src/net-responsibility.conf
i 0755 root root net-responsibility-daemon src/net-responsibility-daemon.ctrl "runlevel(02) start(50) runlevel(03) start(50) runlevel(04) start(50) runlevel(05) start(50) runlevel(00) start(50) runlevel(01) start(50) runlevel(06) start(50)"
```

Now, I took a stab at the line that starts with c since there's a good hint on the website.  Here's what I did there:

```
$ sudo cp net-responsibility.conf /etc/net-responsibility
```

If that's right then :D happy days.  If it's not, could someone lead me in the right direction?

Additionally, I am at a loss of what I need to do when it comes to the line that starts with i.  Yes, I am rather new at some of this stuff even though I have been using Ubuntu for years now.  Can someone help?

Thanks!

semijoyful

---

### Post by semijoyful on 2010-07-18
I went ahead and tried to run the following, but I know I must be missing something...since there's an error:

```
$ sudo net-responsibility-config-cli
/usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require': no such file to load -- /usr/share/net-responsibility/lib/options (LoadError)
	from /usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `require'
	from /usr/local/bin/net-responsibility-config-cli:51

```

Any ideas?

Thanks!

semijoyful

---

### Post by roggan87 on 2010-07-19
Hi semijoyful!

I have no clue why I haven't done this earlier :/ Now the 64-bit version is up on the website. Check out the downloads section and try to run the package called netresponsibility-2.0a1.amd64.deb.

Let me know how it works!
Good luck :)

---

### Post by roggan87 on 2010-07-20
Hi all!

There are still features to add, bugs to fix etc, but I want to pronounce 2.0a2 :)

Note that you have to adjust your configuration for v2.0a2 if you've used another version before.

The most significant feature added in this version is the attached report. As a complement to the usual html-report, the mails can also attach a file that are much easier to view, with a treeview written in JavaScript.

Please feel free to try it out and give feedback. It can be found on the website: [www.netresponsibility.com/download.php](www.netresponsibility.com/download.php)

Be blessed!

---

### Post by huzzak on 2010-07-22
Thanks for making such a useful program!

I'd like to help contribute (particularly with the reports) but I don't know Ruby very well.  I've downloaded the source so that I can poke through it, so maybe I'll be able to get more Ruby experience.

Is there a repository set up somewhere that can be checked out?

Thanks again!

---

### Post by roggan87 on 2010-07-23
> **huzzak said:**
> Thanks for making such a useful program!

I'd like to help contribute (particularly with the reports) but I don't know Ruby very well.  I've downloaded the source so that I can poke through it, so maybe I'll be able to get more Ruby experience.

Is there a repository set up somewhere that can be checked out?

Thanks again!

Hi Huzzak!

I'm glad you volunteer :) Unfortunately there is no repository at the moment.

Maybe I can help you get going, if you tell me what you want to achieve.

Have you tried the newest alpha, v2.0a2? The reports are pretty different compared to v2.0a1.

Good luck!

---

### Post by huzzak on 2010-07-23
Ha ha, thanks Roggan!

I have tried the newest alpha and I like the direction that the reports are going!

I think that my big worry is that since parsing the reports is still pretty difficult and the false-positive rate (since it is only based on the URL) is high that it will make it more tiresome for the people who receive the report to review it.

The best situation would be improving the detection of sites that we don't want visited (and thereby reducing the number of false-positives).  I'm not sure what a good solution to this might be.  I really wish that K-9 had a simple way of plugging into their URL rating system.

Another thing that I think would improve the scanability of the reports and (perhaps) add some additional useful information would be to include a graph of usage over time.  I don't know if times are recorded with the URLS in the database, but it would be very easy to look at and could perhaps expand the user base to include people that don't care about what is being looked at just at what time.  This could be augmented with a "third" dimension coloring the usage according to whether what was being accessed was appropriate or not and black bars indicated that the program was disabled/shutdown.

Does this sound like a good idea?  Is time information available?  Where do you think I should start poking around?  Thanks!

---

### Post by silvertuna on 2010-07-25
I installed 

netresponsibility-2.0a2.amd64.deb (64-bit) (213 KB)

in Lucid Lynx 64-bit.  I get an email report but no text in the body of the email and although the email indicates there is an attachment, no attachment is actually there.

netresponsibility-2.0a1.amd64.deb (64-bit) (211 KB) did generate a report with text in the body of the email.

---

### Post by tetralectic on 2010-07-26
> **silvertuna said:**
> I installed 

netresponsibility-2.0a2.amd64.deb (64-bit) (213 KB)

in Ubuntu Lucid Lynx 64-bit.  I get an email report but no text in the  body of the email and although the email indicates there is an  attachment, no attachment is actually there.

netresponsibility-2.0a1.amd64.deb (64-bit) (211 KB) did generate a report with text in the body of the email.

Many thanks roggan87 for releasing Net Responsibility 2.0a2. However, I  am also having trouble with netresponsibility-2.0a2.amd64.deb in Lucid. I  do get text in the body of the email sent to my Gmail account (and in  accordance with the configuration I have set up for my account on the  Net Responsibility website), but I'm also having trouble with the more  detailed attached report. If I look at my G-mail account my last  attached report is 1392K in size, so I assume it's not an empty file.  However, when I click view I get the error message
>  **My_laptop's Net Responsibility Report**

 Options:  Display time |  Expand all nodes | [Visit www.netresponsibility.com]("http://www.netresponsibility.com/") 

JavaScript has to be enabled. It seems to be blocked by your browser or email host, or anything else.
Please allow JavaScript to see this page correctly. 
  Javascript is enabled in my web browser, so I assume it's a  problem with Gmail or perhaps a bug in  netresponsibility-2.0a2.amd64.deb, can anyone help? When I click on  "Download all attachments" a 129.1 KB zip file is saved to my hard  drive. When I open the zip file in the archive manager there's a 1.4MB  .htm report file in there!!! and a 57 byte file named noname. When I  open the .htm file in Firefox I only get
> **My_laptop's Net Responsibility Report**

 Options:  [Display time]("http://javascript%3Cb%3E%3C/b%3E:displayTime%28true%29") |  [Expand all nodes]("http://javascript%3Cb%3E%3C/b%3E:expandAll%28%29") | [Visit www.netresponsibility.com]("http://www.netresponsibility.com/") , but no actual report underneath this introductory material. This is my report configuration

[IMG]http://farm5.static.flickr.com/4110/4831738419_665bf18640_m.jpg[/IMG]
Notice that although I didn't ask for a zipped attached report, my downloaded attached report was zipped.

Furthermore, when I try to view a duplicate report sent to my mail.com  account, the whole E-mail report, not just the attachment, refuses to  open. I get the error message > "We encountered a technical issue.
Please try again.Net Responsibility reports from 2.0a1 on my  32-bit desktop (without the attachment obviously) open just fine on  mail.com (as well as Gmail).

Also the same netresponsibility-2.0a2.amd64.deb reports sent to to my  pop3 account, and downloaded to my computer using Thunderbird as my mail  client, show nothing in the body of the E-mail as happens for  silvertuna above, and when I try to open the attachment my computer  thinks it's a GIF image, but nothing shows up in the image viewer. If I  save the attachment to the hard drive the file is only 57 bytes in size,  so there's nothing there (I assume that it's the mysterious noname file mentioned above, no .htm file). Does  netresponsibility-2.0a2.amd64.deb not work for pop3 accounts?

I find this quite bewildering, and any help would be greatly appreciated.

---

### Post by roggan87 on 2010-07-27
Hi tetralectic and silvertuna,

Thanks for the feedback!

Please try to copy these two files into /usr/share/net-responsibility/lib/ and see if the reports are getting better.

Regarding Javascript in Gmail; Google automatically rips out all Javascipt if you press "Show", so you'll have to download the file first, before you can see it correctly.

But please try these files before I answer more questions ;)

God bless!

---

### Post by tetralectic on 2010-07-27
> **roggan87 said:**
> Hi tetralectic and silvertuna,

Thanks for the feedback!

Please try to copy these two files into /usr/share/net-responsibility/lib/ and see if the reports are getting better.

Regarding Javascript in Gmail; Google automatically rips out all Javascipt if you press "Show", so you'll have to download the file first, before you can see it correctly.

But please try these files before I answer more questions ;)

God bless!

Hi roggan87

Many thanks for your quick reply. Replacing those two files changed the reports, but it's not working just yet. This is what I get in a long E-mail messages from my Gmail, mail.com and pop3 accounts. The long E-mail message has been truncated.
> [SIZE=-1]**My_laptop <report@netresponsibility.com> **[/SIZE]   [SIZE=-1]** Tue, Jul 27, 2010 at 6:08 AM **[/SIZE]   [SIZE=-1]  
To: [/SIZE]*****[SIZE=-1] 
 [/SIZE]      [SIZE=-1]<style type='text/css'>
body {          /*The text, background, etc.*/
       font-family: verdana;
       font-size: 12px;
}

h1 {            /*The bigger titles. For example Warnings, Shutdowns etc.*/
       font-family: verdana;
       font-size: 15px;
       font-weight: bold;
}

h2 {            /*The smaller titles. Used for blacklist categories and  dates. For example Pornstars, Celebrities and 2009-11-11: (Total: 29)  etc.*/
       font-family: verdana;
       font-size: 12px;
       font-weight: bold;
       color: black;
       display: inline;
}

hr {            /*The line that divides the different parts.*/
       border: solid 1px #CCCCCC;
       height: 1px;
}

.block {
       border: solid #999999;
       border-width: 0 0 0 1;
       margin: 0 0 25 10;
       padding: 0 0 0 5;
}

.whitelist {            /*The matches agains the whitelist. For example [www.netresponsibility.com.*/]("http://www.netresponsibility.com.*/")
       font-family: verdana;
       font-size: 12px;
       font-weight: bold;
       text-decoration: underline;
       font-style: italic;
}

a:link {
       color: #7a94a0;
       font-family: verdana;
       font-size: 12px;
       font-weight: normal;
}

a:hover {
       color: black;
       font-family: verdana;
       font-size: 12px;
       font-weight: normal;
}

a:active {
       color: black;
       font-family: verdana;
       font-size: 12px;
       font-weight: normal;
}

a:visited {
       color: #7a94a0;
       font-family: verdana;
       font-size: 12px;
       font-weight: normal;
}
</style><table><tr><td colspan='2'><b>Info</b></td></tr><tr><td  width='10'>&nbsp;</td><td>      This report is  generated by Net Responsibility. <br>For more information visit  <a href='[http://www.netresponsibility.com/](http://www.netresponsibility.com/)'>[www.netresponsibility.com]("http://www.netresponsibility.com/")</a>. <br><br>Please do not reply to this address ([EMAIL="report@netresponsibility.com"]report@netresponsibility.com[/EMAIL]).</td></tr></table><br><table><tr><td colspan='2'><b>Shutdowns</b></td></tr><tr><td  width='10'>&nbsp;</td><td>      The program has not  been interrupted.</td></tr></table><br><table><tr><td colspan='2'><b>Warnings</b></td></tr><tr><td  width='10'>&nbsp;</td><td>       No matches found  (which is good)</td></tr></table><br><table><tr><td colspan='2'><b>Whitelist</b></td></tr><tr><td  width='10'>&nbsp;</td><td>   No matches with  blacklist <i>and</i>  whitelist</td></tr></table><br><table><tr><td  colspan='2'><b>Attached  report</b></td></tr><tr><td  width='10'>&nbsp;</td><td>       View the attached  file (report_20100727_2.htm) for a better  report.</td></tr></table>--R099@n5Under6@r@Av9r@n5
 @re
Content-Type: multipart/mixed; name="report_20100727_2.htm"
Content-Transfer-Encoding:base64
Content-Disposition: attachment; filename="report_20100727_2.htm"

PGh0bWw+PGhlYWQ+PCEtLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0t
LS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0KfCAgQ29weXJpZ2h0
IG5vdGljZQp8CnwgIChjKSAyMDAzLTIwMDQgVG9iaWFzIEJlbmRlciAodG9i
aWFzQHBocFhwbG9yZXIub3JnKQp8ICBBbGwgcmlnaHRzIHJlc2VydmVkCnwK
fCAgVGhpcyBzY3JpcHQgaXMgcGFydCBvZiB0aGUganNUcmVlIHByb2plY3Qu
IFRoZSBqc1RyZWUgcHJvamVjdCBpcwp8ICBmcmVlIHNvZnR3YXJlOyB5b3Ug
Y2FuIHJlZGlzdHJpYnV0ZSBpdCBhbmQvb3IgbW9kaWZ5CnwgIGl0IHVuZGVy
IHRoZSB0ZXJtcyBvZiB0aGUgR05VIEdlbmVyYWwgUHVibGljIExpY2Vuc2Ug
YXMgcHVibGlzaGVkIGJ5CnwgIHRoZSBGcmVlIFNvZnR3YXJlIEZvdW5kYXRp
b247IGVpdGhlciB2ZXJzaW9uIDIgb2YgdGhlIExpY2Vuc2UsIG9yCnwgIChh
dCB5b3VyIG9wdGlvbikgYW55IGxhdGVyIHZlcnNpb24uCnwKfCAgVGhlIEdO
VSBHZW5lcmFsIFB1YmxpYyBMaWNlbnNlIGNhbiBiZSBmb3VuZCBhdAp8ICBo
dHRwOi8vd3d3LmdudS5vcmcvY29weWxlZnQvZ3BsLmh0bWwuCnwgIEEgY29w
eSBpcyBmb3VuZCBpbiB0aGUgdGV4dGZpbGUgR1BMLnR4dCBkaXN0cmlidXRl
ZCB3aXRoIHRoZXNlIHNjcmlwdHMuCnwKfCAgVGhpcyBzY3JpcHQgaXMgZGlz
dHJpYnV0ZWQgaW4gdGhlIGhvcGUgdGhhdCBpdCB3aWxsIGJlIHVzZWZ1bCwK
fCAgYnV0IFdJVEhPVVQgQU5ZIFdBUlJBTlRZOyB3aXRob3V0IGV2ZW4gdGhl
IGltcGxpZWQgd2FycmFudHkgb2YKfCAgTUVSQ0hBTlRBQklMSVRZIG9yIEZJ
VE5FU1MgRk9SIEEgUEFSVElDVUxBUiBQVVJQT1NFLiAgU2VlIHRoZQp8ICBH
TlUgR2VuZXJhbCBQdWJsaWMgTGljZW5zZSBmb3IgbW9yZSBkZXRhaWxzLgp8
CnwgIFRoaXMgY29weXJpZ2h0IG5vdGljZSBNVVNUIEFQUEVBUiBpbiBhbGwg
Y29waWVzIG9mIHRoZSBzY3JpcHQhCi0tLS0tLS0tLS0tLS0tLS0tLS0tLS0t
LS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0+Cgo8
bWV0YSBodHRwLWVxdWl2PSJjb250ZW50LXR5cGUiIGNvbnRlbnQ9InRleHQv
aHRtbDsgY2hhcnNldD11dGYtOCI+Cjx0aXRsZT5GaXJlZmx5X2xhcHRvcCdz
IE5ldCBSZXNwb25zaWJpbGl0eSBSZXBvcnQ8L3RpdGxlPgoKPHNjcmlwdCBz
cmM9Imh0dHA6Ly93d3cubmV0cmVzcG9uc2liaWxpdHkuY29tL2pzVHJlZS9q
c1RyZWUuanMiIHR5cGU9InRleHQvamF2YXNjcmlwdCIgbGFuZ3VhZ2U9Ikph[/SIZE]

"E-mail truncated" It's nice to see something show up in my pop3 E-mail client (Thunderbird).

I hope this helps

In appreciation

---

### Post by roggan87 on 2010-07-27
Sorry, you got the wrong file :/
I edited my last post and uploaded a new archive. Try that one instead and let me know if it's working...

---

### Post by tetralectic on 2010-07-27
> **roggan87 said:**
> Sorry, you got the wrong file :/
I edited my last post and uploaded a new archive. Try that one instead and let me know if it's working...
Hi roggan87

That's much better. This is the report I received to my Gmail account
> **My_laptop**

 to *** 
show details 10:04 AM (5 hours ago) [IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]

**Info**     This report is generated by Net Responsibility. 

For more information visit [www.netresponsibility.com]("http://www.netresponsibility.com/"). 


Please do not reply to this address ([EMAIL="report@netresponsibility.com"]report@netresponsibility.com[/EMAIL]).
file 
**Shutdowns**     The program has not been interrupted.
**Warnings (1)** **[B]Pornstars_extended** (1)[/B]     [p**lane**t.ubuntu.com/heads/**joey**hg2.+png]("http://planet.ubuntu.com/heads/joeyhg2.+png")
**Whitelist (3)**     [www.netresponsibility.com/lists/**Porn**.bls]("http://www.+netresponsibility.com/lists/Porn.bls")
    [www.netresponsibility.com/lists/**Porn**stars.bls]("http://www.netresponsibility.com/lists/Pornstars.bls")
    
[www.netresponsibility.com/lists/**Porn**stars_extended.bls]("http://www.netresponsibility.com/lists/Pornstars_extended.bls")
**Attached report**     View the attached file (report_20100727_3.htm) for a better report.
[[IMG]https://mail.google.com/mail/images/html2.gif[/IMG]]("https://mail.google.com/mail/?ui=2&ik=960eca58b5&view=att&th=12a157d43680dded&attid=0.1&disp=inline&zw")**report_20100727_3.htm**
102K [COLOR=RoyalBlue]  [/COLOR][COLOR=Black]Open as a Google document   View[/COLOR]   Download and upon clicking on Download, the resulting downloaded .htm file did indeed feature a wonderful, accurate javascript tree of my recent web browsing. Yeah, :p

However, the same report sent to both mail.com and to my pop3 server (using Thunderbird as my mail client) were missing anyway to download the more detailed javascript tree report. This is all I got in both cases
> **Info**    This report is generated by Net Responsibility. 
For more information visit [www.netresponsibility.com]("http://www.netresponsibility.com/"). 

Please do not reply to this address ([EMAIL="report@netresponsibility.com"]report@netresponsibility.com[/EMAIL]).
**Shutdowns**  The program has not been interrupted.
**Warnings (1)** **[B]Pornstars_extended** (1)[/B]    [p**lane**t.ubuntu.com/heads/**joey**hg2.+png]("http://planet.ubuntu.com/heads/joeyhg2.+png")
**Whitelist (3)**   [www.netresponsibility.com/lists/**Porn**.bls]("http://www.%20%20netresponsibility.com/lists/Porn.bls")
    [www.netresponsibility.com/lists/**Porn**stars.bls]("http://www.netresponsibility.com/lists/Pornstars.bls")
   [www.netresponsibility.com/lists/**Porn**stars_extended.bls]("http://www.netresponsibility.com/lists/Pornstars_extended.bls")
**Attached report**   View the attached file (report_20100727_3.htm) for a better report.There were no attached files either. :(

---

### Post by roggan87 on 2010-07-28
Nice to hear it's at least working better, then I'll try to implement it as an option.

Maybe you should try to use the "compress attached report" option. Your server might block html-files, but will allow zip-files?

---

### Post by silvertuna on 2010-07-28
Hi roggan87,

Just tired the fix in #469 and had no effect on my email report.  I see an attachment but there is none to download and no text appears in the body of the email.  FYI, the 2 files i copied were already in the lib folder (they werent missing) so i overwrote them.  I am using Lucid Lynx 64-bit.

PS My reports are going to Yahoo Mail.

---

### Post by tetralectic on 2010-07-28
> **roggan87 said:**
> Nice to hear it's at least working better, then I'll try to implement it as an option.

Maybe you should try to use the "compress attached report" option. Your  server might block html-files, but will allow zip-files?
Hi roggan87
OK, I've just tried that (the zip option), and the results are a little mystifying.

[LIST]
[*]Everything worked fine with Gmail. :D
[*]With  my pop3 account, using Thunderbird as my E-mail client, the E-mail list  flags the E-mail as having an attachment (presumably), but when I open  the E-mail, no attachment is to be found, and the attachment flag in the  E-mail list (indicating an E-mail with an attachment) mysteriously  disappears???? It changed it's mind about there being an attachment when  I opened the E-mail -- weird! :?
[*]With my mail.com webmail account the E-mail was not flagged as having an attachment, nor did it have an attached zip file. :(
[/LIST]
Regarding silvertuna's post #474, I'll get a Yahoo.com webmail account and see what happens for me.

Many thanks

---

### Post by tetralectic on 2010-07-28
> **tetralectic said:**
> Hi roggan87
OK, I've just tried that (the zip option), and the results are a little mystifying.

[LIST]
[*]Everything worked fine with Gmail. :D
[*]With  my pop3 account, using Thunderbird as my E-mail client, the E-mail list  flags the E-mail as having an attachment (presumably), but when I open  the E-mail, no attachment is to be found, and the attachment flag in the  E-mail list (indicating an E-mail with an attachment) mysteriously  disappears???? It changed it's mind about there being an attachment when  I opened the E-mail -- weird! :?
[*]With my mail.com webmail account the E-mail was not flagged as having an attachment, nor did it have an attached zip file. :(
[/LIST]
Regarding silvertuna's post #474, I'll get a Yahoo.com webmail account and see what happens for me.

Many thanks
With the new Yahoo webmail account that I've just set up, I get exactly the same thing happening as silvertuna, namely
> **silvertuna said:**
> Hi roggan87,

Just tired the fix in #469 and had no effect on my email report.  I see  an attachment but there is none to download and no text appears in the  body of the email.  FYI, the 2 files i copied were already in the lib  folder (they werent missing) so i overwrote them.  I am using Lucid Lynx  64-bit.

PS My reports are going to Yahoo Mail.
This is with the zipped file option enabled. There's nothing in the body of the E-mail, and no attachment. Mysteriously, the Yahoo.com E-mail list flags this E-mail as having an attachment. This flag stays in place when  I open and close the empty E-mail report, unlike for my pop3 account with Thunderbird as my E-mail client, where the attachment flag disappears when I open the E-mail, and unlike with my mail.com account which also has no attachment, but also does not flag the E-mail as having an attachment.

---

### Post by tetralectic on 2010-07-28
> **tetralectic said:**
> With the new Yahoo webmail account that I've just set up, I get exactly the same thing happening as silvertuna, namely

This is with the zipped file option enabled. There's nothing in the body of the E-mail, and no attachment. Mysteriously, the Yahoo.com E-mail list flags this E-mail as having an attachment. This flag stays in place when  I open and close the empty E-mail report, unlike for my pop3 account with Thunderbird as my E-mail client, where the attachment flag disappears when I open the E-mail, and unlike with my mail.com account which also has no attachment, but also does not flag the E-mail as having an attachment.
Hi roggan87
I would just add that like silvertuna in post #467, a Net Responsibility2.0a1 report from my 32-bit Jaunty desktop to my new Yahoo.com webmail account gets through without any problems.

---

### Post by huzzak on 2010-08-02
Yesterday my mother looked at the reports and didn't understand them at all.  This was pretty much what I feared would happen.  I brainstormed today and came up with a couple of ways that we could make the reports much more reader friendly.

I also realized that the reports take a long time to generate and a lot of processor power.  I'm assuming this is because the bad words lists are run through all of the URLs and this takes a lot of time (N bad words times M URLs).

The first is to only report domains as a sort of top level executive summary.  I feel like domain names give a pretty good idea of the content of a site without being so overwhelming and confusing.

The second is to display a summary of search results.  I feel like this is a pretty good indicator of what a user is doing online.  I made a mockup of what I think would be a much easier to read report:

[CENTER][IMG]http://img.photobucket.com/albums/v101/Huzzak/Untitled.jpg[/IMG][/CENTER]

The numbers above the horizontal bar are links that connect to anchors down below in the details section.  The details section could have more information than what I showed.  The domains for now probably wouldn't be divided into three groupings.  Same for the keywords.  It shouldn't be hard, however, to quickly make a keyword list for the search terms.  Getting domain information is trickier.  Maybe OpenDNS would help there?

I propose that for now we display all of the search terms and all of the top level domains above the horizontal line.  This will be a vast improvement over the current reports, I think.

I see the algorithm for generating these basic reports going something like the following.  It is obviously rough, but I think it illustrates where we might start and how simple it would be to implement these improvements.

```

domains = []
search_terms = []
for each URL:
	domain = re.match('http://([^/]+).*/', URL)
	domains.add(domain)
	if domain in ['google.com', 'bing.com', 'yahoo.com']:
		search_terms.add(get_search_terms(URL))
generate_report(domains, search_terms)

```

I really feel like this will make the reports much more useful and that it is possible to make this enhancement with minimal effort right now.  I'm interested in any suggestions you guys might have.  Roggan, can you give me some ideas about where to get started in the code to make this happen?

Thanks for all your hard work!

---

### Post by roggan87 on 2010-08-06
Hi!

Sorry I haven't answered in a while. 

Tetralectic and Silvertuna: I'm not sure about why the attachment is failing. I'll have to take a look at it. I will get back if you can help me in any way. My best advise for now is to either use 2.0a1, or 2.0a2 without the attached report.

Huzzak: I really like your idea! I fully agree that the reports must be as easy to understand as possible. Right now it's a bit too much for me to accomplish, but I would be very glad if you tried on your own. I got your personal message as well.

Note that most emailproviders will strip down the html code in email, and using anchors right in the mail will probably cause errors. For some reason random whitespace is inserted into the code, which often causes problems. That's one reason for attaching the report as an html-file. If we want the kind of layout you've presented, it's best to have it in the attached report.

I couldn't resist starting to look at the code. I've attached report.rb in an archive, put it at /usr/share/net-responsibility/lib/report.rb, and overwrite the existing file. I think we'll start with integrating search terms as an attached report part at this stage, and if it's working like we expect we can proceed and change the layout of the report.

Have a look at the method called search_report(). I've only started out for you. You'll have to look at the method warning_report to see how to run the blacklist tests. I guess it's hard to understand how it all works together, but do your best. Ask what you don't understand. We'll probably have to rewrite some methods to suit for this kind of search as well.

Good luck, and hope to hear from you :)

---

### Post by huzzak on 2010-08-06
Thanks, Roggan!

I went through a few tutorials on Ruby online and have been poking through the code so I think that I understand it a little bit better.  The only thing I'm not sure about is debugging and testing the code without *really* running the code and actually sending reports through email.  Is there an easy way to hook into the code so that it outputs reports to a file and doesn't erase everything in the log?  How do you go about testing?

I'm really excited about this, thanks again for all of your work!

---

### Post by roggan87 on 2010-08-06
> **huzzak said:**
> Thanks, Roggan!

I went through a few tutorials on Ruby online and have been poking through the code so I think that I understand it a little bit better.  The only thing I'm not sure about is debugging and testing the code without *really* running the code and actually sending reports through email.  Is there an easy way to hook into the code so that it outputs reports to a file and doesn't erase everything in the log?  How do you go about testing?

I'm really excited about this, thanks again for all of your work!

Nice, I'm really excited as well that you want to help out :)

Well, the text that's right in the email is stored (for testing purpose) in lib/reports/html.htm. The attached file is also temporarily stored in /lib/reports/report_[date]_[i].htm. You can choose name of the attached file with the switch --attachfile or -a, but it will still end up in the same directory. This is good if you don't want to open up a new file every time.

So, if you don't want the program to either send out the mail or clear the log, you can put this line:

```
exit!(0)
```

right *before* the finish line in full_report() in report.rb, that goes like this:

```
style + to_html(html)
```

Good luck, God bless!

---

### Post by roggan87 on 2010-08-07
Huzzak,

Just thought of one more thing. I have to add search_terms to your account since it's not choosable online yet. Note that I'll have to add it every time you're making changes online (no problems for me, but good for you to remember). But I need to know your username. You an just send me a personal message and I'll fix it.

---

### Post by roggan87 on 2010-08-12
Mpnordland, I've sent you a private message.

---

### Post by silvertuna on 2010-08-13
Using 2.0a1, we get a lot of false positives and long strings of urls.  What is the status of making the reports more user-friendly?  Is 2.0a2 better in that regard?  

My problem with 2.0a2 is that the report never actually got attached to the Yahoo email and there was no text in the body of the email. Has that been solved?

---

### Post by roggan87 on 2010-08-13
> **silvertuna said:**
> Using 2.0a1, we get a lot of false positives and long strings of urls.  What is the status of making the reports more user-friendly?  Is 2.0a2 better in that regard?  

My problem with 2.0a2 is that the report never actually got attached to the Yahoo email and there was no text in the body of the email. Has that been solved?

I know, the false-positives is our biggest problem. Unfortunately that haven't been solved yet. Neither has the attachment part, but we're working on these both thing, as they're highest priority of the todo-list.

Thanks for feedback.

---

### Post by silvertuna on 2010-08-13
We appreciate what you are doing.  Thanks!

---

### Post by roggan87 on 2010-08-14
**HELP NEEDED!**

I've tried to rewrite the code a bit, so the attachment is done in python instead of ruby. Before I implement this in the whole program I need to know if it's working better for you guys. All you have to do is to download this archive, unpack it, open a terminal in that directory and run the following command:
```
./report_to your@emailaddress.com
```

Then you'll receive two emails, one with an html-file attached and another with a zip-archive attached. Please open these files to see whether or not JavaScript is working.

Then you just tell me here in this thread or by personal message what email server (like gmail or yahoo) and email client (like Kmail or Thunderbird) you were using and if you got the files, and if they were working. The more different accounts we can try the better!

Thanks a lot people, hope this will work :)

---

### Post by huzzak on 2010-08-14
Both worked for me.  I am using gmail (through Google Apps) as the server and the client.

---

### Post by silvertuna on 2010-08-14
Both worked for me.  Yahoo Mail online.

---

### Post by henjj on 2010-08-20
Hello, I'm trying to set up Net Responsibility on my machine.  I am running Ubuntu 10.04 LTS- the Lucid Lynx.  I downloaded the netresponsibility-2.0a2.deb file and ran the installation.  When I try and send out a report this is the message I get:

joe@joe-desktop:~$ sudo net-responsibility-report
Downloading the configurationfile...
Loading it.
Downloading blacklist for Porn
Downloading blacklist for Pornstars
Downloading blacklist for Models
Downloading blacklist for Celebrities
Downloading blacklist for Pornstars_extended
Downloading blacklist for Models_extended
Downloading blacklist for Celebrities_extended
/usr/share/net-responsibility/lib/options.rb:247:in `update_settings': private method `gsub!' called for nil:NilClass (NoMethodError)
	from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
	from /usr/local/bin/net-responsibility-report:77:in `new'
	from /usr/local/bin/net-responsibility-report:77:in `initialize'
	from /usr/local/bin/net-responsibility-report:135:in `new'
	from /usr/local/bin/net-responsibility-report:135
joe@joe-desktop:~$ 

I have been checking my email and nothing is getting sent out.  Any help would be appreciated.

THanks,

---

### Post by roggan87 on 2010-08-23
> **henjj said:**
> Hello, I'm trying to set up Net Responsibility on my machine.  I am running Ubuntu 10.04 LTS- the Lucid Lynx.  I downloaded the netresponsibility-2.0a2.deb file and ran the installation.  When I try and send out a report this is the message I get:

joe@joe-desktop:~$ sudo net-responsibility-report
Downloading the configurationfile...
Loading it.
Downloading blacklist for Porn
Downloading blacklist for Pornstars
Downloading blacklist for Models
Downloading blacklist for Celebrities
Downloading blacklist for Pornstars_extended
Downloading blacklist for Models_extended
Downloading blacklist for Celebrities_extended
/usr/share/net-responsibility/lib/options.rb:247:in `update_settings': private method `gsub!' called for nil:NilClass (NoMethodError)
	from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
	from /usr/local/bin/net-responsibility-report:77:in `new'
	from /usr/local/bin/net-responsibility-report:77:in `initialize'
	from /usr/local/bin/net-responsibility-report:135:in `new'
	from /usr/local/bin/net-responsibility-report:135
joe@joe-desktop:~$ 

I have been checking my email and nothing is getting sent out.  Any help would be appreciated.

THanks,

Hi Joe!

What is your username? I'll take a look and see if I can find the problem.

---

### Post by roggan87 on 2010-08-24
Henjj,

There is obviously a bug. The whitelist can't be empty at the moment. I recommend you add the following keyword to the whitelist:
```
^(www\.)?netresponsibility\.com
```
since Net Responsibility will download the blacklists from netresponsibility.com, and they will end up in your warnings section unless you whitelist the whole domain. I can guarantee that you won't find any suspected content on netresponsibility.com ;)

Good luck!

---

### Post by henjj on 2010-08-25
Thanks so much for the help!  It is working now.

---

### Post by houndi on 2010-08-26
I haven't been able to solve this error yet, but I don't think that it's serious. Previou sly, I suppressed it, but I'm not comfortable with suppressing error messages.

---

### Post by mpnordland on 2010-09-06
Hi, I have fixed my computer now, and I will be taking a look at the send_report.py, I really need this program, so I am excited to help!

---

### Post by mpnordland on 2010-09-06
Hi, I'm back again, I found a bug, in send_report.py, even if the debug arg is "False" it prints debug info. I have fixed it.  I have also tried to consolidate the code into individual functions to make the code more human readable I'm still working on it, but i post it here to show roggan87
also, the test.conf incuded in the python_attachment.tar.gz file didn't have the email_to field, but i added it so everything worked.
 [ATTACH]168711[/ATTACH]

---

### Post by mpnordland on 2010-09-06
Back again! I have now fixed another bug, that split up the "send_to" email address when creating the message, this bug however did not mess with the sending of the report. I have also finished consolidating the code into functions, and everything still works. attached is my modified version of the original python_attachment.tar.gz don't forget to change the "send_to" email address in the test.conf file.
[ATTACH]168718[/ATTACH]

---

### Post by roggan87 on 2010-09-09
Thanks mpnordland for your help in this!

I'll take a look at this and include it in the next release. Regarding the config file without email_to, the script ```
./report_to [email_address]
``` adds email_to: [email_address] in the config file before sending the reports. It's not actually a bug, but if you're using the actual command ```
python send_report.py ...
``` then you need to manually add email_to. Hope that explains.

Once again, thank you!

---

### Post by mpnordland on 2010-09-09
> **roggan87 said:**
> Thanks mpnordland for your help in this!

I'll take a look at this and include it in the next release. Regarding the config file without email_to, the script ```
./report_to [email_address]
``` adds email_to: [email_address] in the config file before sending the reports. It's not actually a bug, but if you're using the actual command ```
python send_report.py ...
``` then you need to manually add email_to. Hope that explains.

Once again, thank you!

oh, that´s good to know.

---

### Post by mrgronk on 2010-09-23
Hi all,

I'm new to the whole Net Responsibility thing - I just downloaded it and set it up a day or two ago. I'd like to start by thanking those who've put a lot of time and effort into it over the years to get it to where it now is.

Anyway, I had a couple of questions about it.

First, I haven't yet played around with Ruby as a language, but I'm reasonably familiar with programming in general, such that I may be able to help a little with client-side stuff, if time permits. What would be the best way of doing so? I understand there's no generally accessible repo at the moment?

Second, and more importantly, is there such a thing as a central blacklist of domain names? I haven't been able to identify one as such. Regrettably, I'm sure we can all think of examples of web sites where the domain name is innocuous and even the full URL won't necessarily trigger an alert. That is, using a contrived example, a URL such as "http://www.dodgydomain.com/images/2010/09/23/016.jpg" - would that trigger an alert, without the recipient of reports trawling through the whole extended list *and* knowing in advance that [www.dodgydomain.com](www.dodgydomain.com) is a red flag?

I know that there's the "personal blacklist" option, which can be used in a pinch, and as posters above have said in the final analysis it's about the user's heart and intentions. I also know that trying to maintain a full list of bad domains is impossible, like a neverending game of whack-a-mole. Nevertheless, I'm sure there are lists out there that would give us a good starting point, and sites could be, as it were, submitted for consideration. (Perhaps another list that could be modified that way is the ever-growing list of performers.)

Maybe all this is irrelevant; perhaps the functionality already exists (I haven't been game to go to a known dodgy website in the last day or two and see whether the incident gets reported). Nevertheless, it's a concern I have, as I wonder about the existence of a fairly large loophole. I'd welcome the thoughts of the maintainers on this matter.

---

### Post by mpnordland on 2010-09-23
Hi mrgronk, 
The answer is yes, all those "blacklist" categories that you can select from when you register are the central blacklist, if you come up against a bad site you can blacklist it personally, but right now there is now way (except maybe to post it here) to get it on in one of those categories
I hope this helps,
Micah

---

### Post by mpnordland on 2010-10-01
Hi, again,
As known by roggan87 (but no one else) I have been working on a gui for net responsibility.
and, ver 1 is mostly done, I have uploaded it so that you guys can check it out, it requires that [wxPython]("http://www.wxpython.org/") be installed, currently it is set up to use the "dummy_config.py" file included, but if you comment out line 60, and uncommented line 57 you could use it to run the real net responsibility configuration. note, right now it will not warn you if there is nothing in the username or password boxes, it probably wont crash, but it won't do anything either. Have fun!
[ATTACH]171001[/ATTACH]

---

### Post by tetralectic on 2010-10-01
> **mpnordland said:**
> Hi, again,
As known by roggan87 (but no one else) I have been working on a gui for net responsibility.
and, ver 1 is mostly done, I have uploaded it so that you guys can check it out, it requires that [wxPython]("http://www.wxpython.org/") be installed, currently it is set up to use the "dummy_config.py" file included, but if you comment out line 60, and uncommented line 57 you could use it to run the real net responsibility configuration. note, right now it will not warn you if there is nothing in the username or password boxes, it probably wont crash, but it won't do anything either. Have fun!
[ATTACH]171001[/ATTACH]Hi mpnordland

It's very nice! This GUI will make a great addition to Net Responsibility and I'm looking forward to it being released with a future version of NR

:P:P

---

### Post by mpnordland on 2010-10-02
> **tetralectic said:**
> Hi mpnordland

It's very nice! This GUI will make a great addition to Net Responsibility and I'm looking forward to it being released with a future version of NR

:P:P

Well thanks, I did all this week, and, there still are a few layout issues, as you may have noticed, when the "dummy_config.py" script finishes the "confiugration finished" text appears in the main window right on top of the "username" text. resize the window and the text is placed correctly, (sigh) and I need to add a mechanism to prevent the config from being run without there being any input in the text boxes.
I'm glad you like it. (sort of a long read to get to that!)

---

### Post by roggan87 on 2010-10-04
> **mpnordland said:**
> Hi, again,
As known by roggan87 (but no one else) I have been working on a gui for net responsibility.
and, ver 1 is mostly done, I have uploaded it so that you guys can check it out, it requires that [wxPython]("http://www.wxpython.org/") be installed, currently it is set up to use the "dummy_config.py" file included, but if you comment out line 60, and uncommented line 57 you could use it to run the real net responsibility configuration. note, right now it will not warn you if there is nothing in the username or password boxes, it probably wont crash, but it won't do anything either. Have fun!
[ATTACH]171001[/ATTACH]

Really nice mpnordland!
I'm looking forward to include this feature in the next release. It worked well with dummy_config except for the "Configuration Finished" text as you've mentioned.

I also tried to uncomment line 57 and 58, but ran into the following problem:
```
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "main.py", line 57, in run
    script=subprocess.Popen("net-responsibility-config-cli --setusername "+username+" --setpassword "+password,
NameError: global name 'username' is not defined
```

Just thought I'd let you know, other than that I'm impressed :)
Keep up the good work!

---

### Post by mpnordland on 2010-10-04
> **roggan87 said:**
> Really nice mpnordland!
I'm looking forward to include this feature in the next release. It worked well with dummy_config except for the "Configuration Finished" text as you've mentioned.

I also tried to uncomment line 57 and 58, but ran into the following problem:
```
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "main.py", line 57, in run
    script=subprocess.Popen("net-responsibility-config-cli --setusername "+username+" --setpassword "+password,
NameError: global name 'username' is not defined
```Just thought I'd let you know, other than that I'm impressed :)
Keep up the good work!
I'll look into that, and can anybody test it on KDE, I use gnome, and I want to make sure that everything looks the same, also, I had a name idea for this gui (other than "net-responsibility-gui") here it is: Responsibility Wrench. Tell me what you think of it!

---

### Post by mpnordland on 2010-10-04
I fixed the problem. Silly me, I used the wrong variable name lol. here's the fixed version
EDIT: in fixing that problem I encountered another, I am going to try and fix it right away, what the bug is: python's subprocess module can't find the file "net-responsibility-config-cli" which means that it can't figure out the command. I think that I can fix this real soon though, python is SOOO easy!

edit again! I just switched to a new computer, and I hadn't installed net responsibility, so, once it's installed, I'll try out the gui configuring it!

---

### Post by mpnordland on 2010-10-07
Hi
It seems like I'm the only one who ever posts to this thread!
any way, I have fixed all the issues in the gui, and I hearby declare that the first version is complete. 
I have attached the files, and of course, the dummy script!

---

### Post by roggan87 on 2010-10-08
> **mpnordland said:**
> Hi
It seems like I'm the only one who ever posts to this thread!
any way, I have fixed all the issues in the gui, and I hearby declare that the first version is complete. 
I have attached the files, and of course, the dummy script!

Hi Micah!

Sorry about being late to answer :/
I think your gui is awesome! It's gonna be a nice feature. I was testing the latest release, and it looked great with the dummy script. Unfortunately it didn't work completely with net-responsibility-config-cli, even though it was much better than the earlier version. This is my output:
```
/usr/local/bin/net-responsibility-config-cli:93:in `gets': No such file or directory -  --setusername roggan87 (Errno::ENOENT)
        from /usr/local/bin/net-responsibility-config-cli:93:in `initialize'
        from /usr/local/bin/net-responsibility-config-cli:128:in `new'
        from /usr/local/bin/net-responsibility-config-cli:128

```
So I tried to teak your script a little, and edited line 57 to look like the following:
```
script=subprocess.Popen(["net-responsibility-config-cli","--setusername",self.user,"--setpassword",self.password], stdout=subprocess.PIPE)
```
And it got better, but still not perfect. Net Responsibility Config received these values:
```
--setusername roggan87 --setpassword <bound method TextCtrl.GetValue of <wx._controls.TextCtrl; proxy of <Swig Object of type 'wxTextCtrl *' at 0x211e710> >>
```

Other then that it was looking really good!
God bless :)

---

### Post by mpnordland on 2010-10-08
Hi, I fixed that, it was a syntax mistake. easy to spot, easy to fix!

---

### Post by tetralectic on 2010-10-08
> **mpnordland said:**
> Hi
It seems like I'm the only one who ever posts to this thread!
any way, I have fixed all the issues in the gui, and I hearby declare that the first version is complete. 
I have attached the files, and of course, the dummy script!
Hi mpnordland
> It seems like I'm the only one who ever posts to this thread!
I'm following following what you are doing with much interest and I appreciate your (and [roggan87]("http://ubuntuforums.org/member.php?u=796965")) posts. The GUI will add much to the finished feel of Net Responsibility.

At the moment though, I'm a little distracted since, as of last Thursday, I'm "between jobs".

In appreciation

tetralectic

---

### Post by mrgronk on 2010-10-10
Hi again,

So I've done what was suggested earlier and have put some entries in my personal blacklist.

While mucking around with blacklists, I accidentally deleted my sole whitelist entry, being (www)?.netresponsibility.com. So I re-added it, and at the same time I inadvertently added the empty string to my whitelist.

This meant that, every time I tried to send a report, it would fail - after spending a lot of time (and CPU effort) processing the strings.

When I tried "sudo /usr/local/bin/net-responsibility-report --testmail", I got a stack trace. I've added the terminal output (combined STDOUT and STDERR, I suppose) as a text file. In brief, though, the proximate cause of the error was:

yaml.scanner.ScannerError: while scanning a block scalar
  in "/etc/net-responsibility.conf.tmp", line 84, column 12
expected chomping or indentation indicators, but found '^'
  in "/etc/net-responsibility.conf.tmp", line 84, column 13

This stemmed from a line in the downloaded conf file, viz.:

whitelist: |^([www.)?netresponsibility.com](www.)?netresponsibility.com)

From what I can gather, because there was nothing but whitespace before the | character, the YAML parser (over which we have no control) was thrown into confusion, and the entire thing failed in an unhelpful manner.

Those who have control over the website: would it be possible to tweak it so that an inadvertent addition of the empty string (or, I suppose, a string containing only whitespace) to either the whitelist or the blacklist returns an error?

Thanks!

---

### Post by mrgronk on 2010-10-10
I've also taken the liberty of making a few patches to clean up some problems I found.

First is the complaint about the SQLite3::BusyException. That, I think, was due to queries being opened and their results never closed, in lib/modules/db.rb. I've attached a patch (prepared with "diff -u") for that file, in which opened queries are closed. That's called "db_patch.txt". I'm not sure I've done that everywhere it needs to be done; but I think at least I got all the "queries". Perhaps there are some canonical test cases against which the patch can be checked.

Second is a rather strange bug I found in send_report.py. If an e-mail is going to multiple addresses, the "To:" header would just work, because the list of recipients came back as a list. But if it was just a single e-mail address, the join function would end up turing the "To:" into, e.g., "j, o, e, @, b, l, o, g, g, s, ., c, o, m". The attached "send_report_patch.txt" should fix this. The caveat here is that I don't know if I properly handled the case in which the list of addresses is neither a string nor a list. I asked it to print a message and raise an exception. Is that correct?

The third thing was in "lib/report.py", where I just made a couple of cosmetic changes (e.g., removing a foreign language phrase and replacing it with a hopefully more descriptive English one). That's in "report_patch.txt".

Let me know if these are OK / not OK.

---

### Post by mrgronk on 2010-10-10
Finally, reports keep getting flagged as Spam by my e-mail provider (I get a copy of my reports sent to me, so that if at any time I'm asked about a particular entry I can, in principle, see what is being referred to). The spam filter gives this reason:

X-Spam-Report:  Content analysis details: 1.0 EXTRA_MPART_TYPE       Header
 has extraneous Content-type:...type= entry 1.7 INVALID_DATE          
 Invalid Date: header (not RFC 2822) 0.0 TO_MALFORMED           To: has a
 malformed address 1.4 DATE_IN_PAST_03_06     Date: is 3 to 6 hours before
 Received: date 0.0 HTML_MESSAGE           BODY: HTML included in message
 1.7 MIME_HTML_ONLY         BODY: Message only has text/html MIME parts 0.9
 MIME_HEADER_CTYPE_ONLY 'Content-Type' found without required MIME headers
 1.1 HTML_MIME_NO_HTML_TAG  HTML-only message, but there is no HTML tag 2.6
 INVALID_MSGID          Message-Id is not valid, according to RFC 2822


Does any of this make sense to anyone? Also why I would be getting attachments called "attachment.dat" which the system thinks are GIF files?

I'm using Evolution as my e-mail client, if that helps. I currently know next to nothing about MIME types, other than that they exist (and that the MIME type doesn't necessarily correspond to the file extension).

---

### Post by McMurdo on 2010-10-11
> **tetralectic said:**
> Hi mpnordland

I'm following following what you are doing with much interest and I appreciate your (and [roggan87]("http://ubuntuforums.org/member.php?u=796965")) posts. The GUI will add much to the finished feel of Net Responsibility.

At the moment though, I'm a little distracted since, as of last Thursday, I'm "between jobs".

In appreciation

tetralectic

I'm stalking this thread, too. Somewhat stuck in XP at the moment, though.

---

### Post by roggan87 on 2010-10-11
> **mpnordland said:**
> Hi, I fixed that, it was a syntax mistake. easy to spot, easy to fix!

Now it's running like a charm!
I still have to edit line 57 though, to look like the following:
```
script=subprocess.Popen(["net-responsibility-config-cli","--setusername",self.user,"--setpassword",self.password], stdout=subprocess.PIPE)
```

Do you know if there's any way to catch error messages in the gui? I mean, if the gui can display error messages from net-responsibility-config-cli?

> I've also taken the liberty of making a few patches to clean up some problems I found.

First is the complaint about the SQLite3::BusyException. That, I think, was due to queries being opened and their results never closed, in lib/modules/db.rb. I've attached a patch (prepared with "diff -u") for that file, in which opened queries are closed. That's called "db_patch.txt". I'm not sure I've done that everywhere it needs to be done; but I think at least I got all the "queries". Perhaps there are some canonical test cases against which the patch can be checked.

Second is a rather strange bug I found in send_report.py. If an e-mail is going to multiple addresses, the "To:" header would just work, because the list of recipients came back as a list. But if it was just a single e-mail address, the join function would end up turing the "To:" into, e.g., "j, o, e, @, b, l, o, g, g, s, ., c, o, m". The attached "send_report_patch.txt" should fix this. The caveat here is that I don't know if I properly handled the case in which the list of addresses is neither a string nor a list. I asked it to print a message and raise an exception. Is that correct?

The third thing was in "lib/report.py", where I just made a couple of cosmetic changes (e.g., removing a foreign language phrase and replacing it with a hopefully more descriptive English one). That's in "report_patch.txt".

Let me know if these are OK / not OK.

Thanks for your patches! I haven't tried them out yet though. Actually in lib/report.rb the following line
```
info = [:folder => "Info", :empty => "Testar lite nya varianter..."]#:empty => @options.info]

```
Should be:
```
info = [:folder => "Info", :empty => @options.info]

```

It's a mistake by me. The issue you've addressed with send_report.py might be fixed. mpnordland have been taking a good look at this. The same thing goes with the report as spam. I'll try to release a new version soon with some updates, hopefully this'll be fixed.

Regarding the whitelist bug I'll take a look on it. The personal lists are still quite buggy. I hope this'll get better. I tried to fix the problem for you, otherwise you should be able to log in and check the upper "delete checkbox" (that precedes an empty line) in the personal whitelist area.

Thanks for feedback and bud-reports, God bless!

---

### Post by mpnordland on 2010-10-12
Hi, wow, alot has happened while I was gone!
@mrgronk 
1. thanks for fixing sglite error that has bugged me in the past.
2. please post your modified version of send_report.py and mark your changes with comments
@roggan87
1. all errors will come out in the output panel in the dialog that pops up when you hit the configure button
2. theoretically both mine and yours should work, but seeing as I don't have the development version installed, I can't test the actual config script. I have replaced my line with yours, and that should make just one thing to do: make it possible just to hit enter when you've entered your credentials.
well, TTFN! Ta Ta For Now! :)

---

### Post by roggan87 on 2010-10-12
Alright people, I've released a new version on the website, called 2.0a3. The biggest differencies from 2.0a2 is:
- Graphic User Interface for the configuration, made by mpnordland
- Shouldn't bug out if the personal whitelist is empty
- The attached report should work with more email providers, much thanks to mpnordland
- The db_patch attached by mrgronk is implemented, which means the SQLite3::BusyException is finally solved. Many thanks!

A note on shortcut to GUI: In KDE I had to edit the meny entry to run it as root, otherwise it wouldn't run.

Good luck with this version!
Roggan

---

### Post by mpnordland on 2010-10-13
well, good thing this is still alpha!
Roggan, there is a rather fatal flaw in the shortcut. In Gnome, for GUI apps, gksu is the command to use instead of sudo, if you still want to use sudo, then set terminal to "true", else, use gksu(on gnome) I don't know about KDE. If these mod aren't made, plain and simple, it won't work.

---

### Post by tetralectic on 2010-10-13
> **roggan87 said:**
> Alright people, I've released a new version on the website, called 2.0a3. The biggest differencies from 2.0a2 is:
- Graphic User Interface for the configuration, made by mpnordland
- Shouldn't bug out if the personal whitelist is empty
- The attached report should work with more email providers, much thanks to mpnordland
- The db_patch attached by mrgronk is implemented, which means the SQLite3::BusyException is finally solved. Many thanks!

A note on shortcut to GUI: In KDE I had to edit the meny entry to run it as root, otherwise it wouldn't run.

Good luck with this version!
Roggan
Hi Roggan

I just installed Net Responsibility on Ubuntu 10.04 64-bit and could not find the configuration launch buttons (GUI or CLI) anywhere in the gnome main menu bar :(

The  installation output is ```
sudo dpkg -i netresponsibility-2.0a3.amd64.deb
Selecting previously deselected package netresponsibility.
(Reading database ... 460302 files and directories currently installed.)
Unpacking netresponsibility (from netresponsibility-2.0a3.amd64.deb) ...
Setting up netresponsibility (2.0a3) ...
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
update-rc.d: warning: net-responsibility-daemon start runlevel arguments (2) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: net-responsibility-daemon stop runlevel arguments (0) do not match LSB Default-Stop values (0 1 6)
 * Starting the Net Responsibility daemon net-responsibility-daemon             /etc/init.d/net-responsibility-daemon: Starting net-responsibility-daemon
                                                                         [ OK ]

Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
```I don't see the problem flagged in this output.

I ended up making my own main menu launch buttons and the configuration (both CLI & GUI) worked just fine resulting in a successful --testmail report.

As mpnordland noted previously
> **mpnordland said:**
> Hi, again,
As known by roggan87 (but no one else) I have been working on a gui for net responsibility.
and, ver 1 is mostly done, I have uploaded it so that you guys can check it out, it requires that [wxPython]("http://www.wxpython.org/")  be installed, currently it is set up to use the "dummy_config.py" file  included, but if you comment out line 60, and uncommented line 57 you  could use it to run the real net responsibility configuration. note,  right now it will not warn you if there is nothing in the username or  password boxes, it probably wont crash, but it won't do anything either.  Have fun!
[ATTACH]171001[/ATTACH]
the gui does not alert you if there is nothing in the username or  password boxes, or if the username and/or password are incorrect.  Also a minor points, perhaps the username or  password boxes in the GUI could be a little longer and a close GUI button added.

Aside from this, many thanks mpnordland for the GUI and email providers improvements :P

Many thanks to mrgronk for db_patch :P

And many thanks roggan87 for Net Responsibliity 2.0a3 :P

---

### Post by tetralectic on 2010-10-14
> **roggan87 said:**
> Alright people, I've released a new version on the website, called 2.0a3. The biggest differencies from 2.0a2 is:
- Graphic User Interface for the configuration, made by mpnordland
- Shouldn't bug out if the personal whitelist is empty
- The attached report should work with more email providers, much thanks to mpnordland
- The db_patch attached by mrgronk is implemented, which means the SQLite3::BusyException is finally solved. Many thanks!

A note on shortcut to GUI: In KDE I had to edit the meny entry to run it as root, otherwise it wouldn't run.

Good luck with this version!
Roggan
With 2,0a3 on 64-bit Lucid 10.04, I'm getting the attached report (zipped) making it through to Thunderbird from my pop3 account, to Gmail, Yahoo, and Mail.com, and the body of the E-mail report is just fine (complete with one or two false positives) :) My Net Responsibility settings on the web site are set to send the "Complete history" in the attached file. However after opening the attachment I see only
> My Net Responsibility Report
Options: Display time | Expand all nodes | Visit [www.netresponsibility.com]("http://www.netresponsibility.com")  there is no javascript tree of my web surfing activities on any of the above E-mail accounts. :(  I have surfed the web plenty today, so this surfing list should be long.

To summarize: the zipped E-mail attachment makes it through to all of the E-mail accounts I have tried so far, but sadly the actual "Complete history" javascript tree is missing. This includes G-mail, for which the attached report and javascript tree came through without a problem in 2.0a2.

---

### Post by roggan87 on 2010-10-14
Thank you guys for feedback!
> Roggan, there is a rather fatal flaw in the shortcut. In Gnome, for GUI apps, gksu is the command to use instead of sudo, if you still want to use sudo, then set terminal to "true", else, use gksu(on gnome) I don't know about KDE. If these mod aren't made, plain and simple, it won't work. 

Fixed. I've uploaded the new files to the website. It seems to work in KDE as well.

> To summarize: the zipped E-mail attachment makes it through to all of the E-mail accounts I have tried so far, but sadly the actual "Complete history" javascript tree is missing. This includes G-mail, for which the attached report and javascript tree came through without a problem in 2.0a2.

Wonder why this is happening? It's working as it should for me. Are you sure the daemon is running? Otherwise you could try to uninstall Net Responsibility and install it again. Hope you'll get it working!

Roggan

---

### Post by mpnordland on 2010-10-14
@tetraletic: are you sure you have the complete history options chosen on the website? that might be the problem.

---

### Post by mpnordland on 2010-10-14
how strange, I just checked my report, and while, the emailed report is there, in the attachment, it says that JavaScript is disabled, when it, in fact is on. I know, I checked. this is weird, I haven't had this before, maybe it isn't(JavaScript turned off), Maybe I don't have it installed, but I thought I did, so I will check. 
ps, I tested it in both chromium and Firefox.

---

### Post by mpnordland on 2010-10-14
the gui does not alert you if there is nothing in the username or  password boxes, or if the username and/or password are incorrect.  
@ telatiric
the gui should alert you, maybe I didn't upload that one...
hmm. when you click the configure button, it just runs the old config script, and it will mention if the credentials aren't right in the out put panel, I just saw this, so this may seem out of place.

---

### Post by mpnordland on 2010-10-14
> **mpnordland said:**
> how strange, I just checked my report, and while, the emailed report is there, in the attachment, it says that JavaScript is disabled, when it, in fact is on. I know, I checked. this is weird, I haven't had this before, maybe it isn't(JavaScript turned off), Maybe I don't have it installed, but I thought I did, so I will check. 
ps, I tested it in both chromium and Firefox.

ok, I figured that out, I had to download it. I also found out that I am afflicted with the same problem as teltratic, there is nothing but the header, I am going to examine this more closely.

---

### Post by mpnordland on 2010-10-14
ok, we have a JavaScript error here, I looked at the source of the attached report, and the list was there all right, but nothing shows up when the pages is displayed. I don't know JavaScript, but I'll try and find the problem.

a little bit later ...
ah, never mind, i can't make heads or tails of it.

---

### Post by tetralectic on 2010-10-14
> **roggan87 said:**
> Thank you guys for feedback!
...
Wonder why this is happening? It's working as it should for me. Are you sure the daemon is running? Otherwise you could try to uninstall Net Responsibility and install it again. Hope you'll get it working!

Roggan
Yes the daemon is running. In fact the body of the report displays some false positives[IMG]http://farm5.static.flickr.com/4059/5081241016_763703508c_z.jpg[/IMG]
so the daemon is definitely running. And yet theres no javascript tree in the attached file

[IMG]http://farm5.static.flickr.com/4028/5081240922_3bd8437062.jpg[/IMG]
> **mpnordland said:**
> @tetraletic: are you sure you have the  complete history options chosen on the website? that might be the  problem.Yup I have the "Complete history" option chosen on the website

[IMG]http://farm5.static.flickr.com/4105/5080647055_43cc07be8d_m.jpg[/IMG]
And Synaptic show that I am running 2.0a3 :confused:

Many thanks to all who all who are working on and have worked on Net Responsibility :)

---

### Post by mpnordland on 2010-10-14
Just in case you didn't notice, I am having this prob too, This is a must fix, I wonder what's wrong.

---

### Post by tetralectic on 2010-10-14
> **mpnordland said:**
> ok, we have a JavaScript error here, I looked at the source of the attached report, and the list was there all right, but nothing shows up when the pages is displayed. I don't know JavaScript, but I'll try and find the problem.

a little bit later ...
ah, never mind, i can't make heads or tails of it.
Thanks mpnorland. When I open up my report in a text editor I also see my report wrapped in javascript. It just doesn't render.

---

### Post by roggan87 on 2010-10-14
@mpnordland or @tetralectic or anyone else that's having problems with this:

Could you please forward one of the non-working attached files to me, so I can have a look at it?
You can reach me at
robertrosman [at] gmx [dot] com
Thanks

---

### Post by mpnordland on 2010-10-15
I must note another bug: while in the reports the "to:" addresses are correct in the report, in the test mail are all split up again,:-k
anyway, in terms of improvments: I am already started on adding more features to the gui, currently, a new test mail button has been added, and I plan to add a "Report" button as well. That should make the gui do all that the cli can do, and I want to make it possible to also edit personal whitelists/blacklists there as well, basically I want eventually make it THE place to configure EVERYTHING about Net Responsibility.
Yes, I know, I am ambitious, but I think that this is possible with help from Roggan.
That's all from the Asylum, be back when there's more news!

---

### Post by roggan87 on 2010-10-16
Hi!
I think I've found the bug you've noticed (in the attached files). It should be fixed in the files on the website. It might not work with the first report you send, but in all the following.

@Mpnordland: Have you tried if it works with only one email_to address? Otherwise that might be the problem,

I like your ambitions mpnordland, and I hope we can make it work, shouldn't be impossible.

Take care guys!

---

### Post by mpnordland on 2010-10-16
actually, there is only one email address for the test mail, so, I don't know...
I'll go have a look.

---

### Post by mpnordland on 2010-10-16
bug fixed, in send_report.py, line 75:

toaddrs = config['email_to']

need's to be:

toaddrs = [config['email_to']]

the reason being is that in python, most "list" methods, also work on strings. This is because a string can also be thought of as a "list" of characters, like in C. "toaddrs = config['email_to']" places a string in to "toaddrs" and then the line "msg['To'] = ", ".join(toaddrs)" takes each character of the string and places a comma and a space after it(unless it is a list, then things work like they should) and makes a new string out of them.
Do I make sense? I hope I do. If I don't, tell me! I don't know, but this may foul up reports to multiple addresses, if so, I have an idea to fix that as well, I'll have to test that.

---

### Post by mpnordland on 2010-10-16
yep it does, I'll get to work on that fix right away!

---

### Post by mpnordland on 2010-10-16
And I have it fixed. It's not a big change, but it does make things come up nicer in the o l' email inbox :)

---

### Post by roggan87 on 2010-10-17
Thanks Micah!
I've recompiled and uploaded the packages on the websites.

Robert

---

### Post by mpnordland on 2010-10-18
glad to help

---

### Post by mpnordland on 2010-10-21
Hi,
I've added those buttons, and I've added support for hitting enter when you're done entering config credentials, also, as asked, I have made the text boxes longer, and I think that it is an improvement as well. I had had a lingering suspicion that the method I was using to get the output of the net-responsibility-config-cli was actually waiting to print the output until it was finished. I now know that for a fact, and I am working on a real time way to do this. Also, all ruby error messages also show up in the gui, as I have redirected the stderr to stdout. So, I guess ver. 2 of net-responsibility-gui is in development :)
Anybody with knowledge of python's subprocess and select modules could be of service.

---

### Post by roggan87 on 2010-10-23
> **mpnordland said:**
> Hi,
I've added those buttons, and I've added support for hitting enter when you're done entering config credentials, also, as asked, I have made the text boxes longer, and I think that it is an improvement as well. I had had a lingering suspicion that the method I was using to get the output of the net-responsibility-config-cli was actually waiting to print the output until it was finished. I now know that for a fact, and I am working on a real time way to do this. Also, all ruby error messages also show up in the gui, as I have redirected the stderr to stdout. So, I guess ver. 2 of net-responsibility-gui is in development :)
Anybody with knowledge of python's subprocess and select modules could be of service.

Sounds really nice!
Looking forward to try it out :)
Keep it up,
Roggan

---

### Post by mpnordland on 2010-10-27
Also, something I have noticed, aol webmail (which my brother uses) comes back with a lot of false positives, This needs some attention, but it is a minor issue.

---

### Post by mpnordland on 2010-11-04
Hi, I have made some advances, the rewrite of the processing code is done, and working, configuration is currently broken, testmail and report buttons work. Roggan, somehow, with the same command that I was using before, now doesn't work, what ever it does, it ignores the --setusername and --setpassword args and proceeds with the regular cli config, which won't work because you can't input text to the text box.

---

### Post by roggan87 on 2010-11-05
> **mpnordland said:**
> Hi, I have made some advances, the rewrite of the processing code is done, and working, configuration is currently broken, testmail and report buttons work. Roggan, somehow, with the same command that I was using before, now doesn't work, what ever it does, it ignores the --setusername and --setpassword args and proceeds with the regular cli config, which won't work because you can't input text to the text box.

Cool. I got your email as well. Don't panic about getting it working, even though I'm looking forward to implement it :)

I wonder what the problem is? I had to edit the line that calls net-responsibility-config-cli in order to make it work. What happens if you just run the command ```
net-responsibility-config-cli --setusername [username] --setpassword [password]
``` directly in a terminal? Also remember that it only works in the latest version (2.0a3).

Good luck!

---

### Post by mpnordland on 2010-11-09
yup, tried that. It worked. In the gui, it don't. I'm not sure why, we'll have to look closely at this. I have internet at my house now, so we can work on this more hand-in-glove.

---

### Post by Nicodemus144 on 2010-11-11
Hi guys, can you help me out? I have some questions regarding net responsibility.  I'm using Ubuntu 10.04 64-bit.

1) I'm trying to upgrade to the 64-bit 2.0a3 version from this prior version: netresponsibility-svn.20080703023549.deb.  When I try to install 64-bit 2.0a3 from the .deb file I keep receiving an error that states a more current version is already installed and it won't let me proceed. Can you help me resolve this error?

2) Is there anything special I need to know about uninstalling? I just did a search for all files and directories with the word responsibility and deleted them, then rebooted.

3) If the net-responsibility-daemon is running will it appear in the process list of the task monitor?

4) Do I still need to create cron jobs to automate the net responsibility report, or does automatic reporting work now?

Thank you for all you help, time, patience and hard work!  This project means a lot to me and I'm sure many others!

---

### Post by mpnordland on 2010-11-11
ok, clarify something for me.
You installed net responsibility by building a package from the svn?
well then, you can go to synaptic(or software-center) and search for "netresponsibility". The package should come up. next simply completely remove it so that it removes the config file. Then install the latest version from the website ([www.netresponsibility.com]("http://www.netresponsibility.com/")) 
configure net responsibility with our new gui! 
Your all set! Automatic reports, are working, and the database error is fixed. We're glad net responsibility helps.

---

### Post by Nicodemus144 on 2010-11-11
thanks for the quick response!

the svn .deb package i am referring to i got from your download page a long time ago.

[http://www.netresponsibility.com/download.php](http://www.netresponsibility.com/download.php)

Alternative Version 0.5.0:
--If none of the above files are working for you, you can try this one (64-bit version).

i'll try what you suggest once i get home.  i'd love to not have to reinstall ubuntu! =)

also, can you answer question 3 for me?

3) If the net-responsibility-daemon is running will it appear in the process list of the task monitor?

i'm just trying to make sure it's all working correctly.

thanks!

---

### Post by tetralectic on 2010-11-11
> **Nicodemus144 said:**
> thanks for the quick response!

the svn .deb package i am referring to i got from your download page a long time ago.

[http://www.netresponsibility.com/download.php](http://www.netresponsibility.com/download.php)

Alternative Version 0.5.0:
--If none of the above files are working for you, you can try this one (64-bit version).

i'll try what you suggest once i get home.  i'd love to not have to reinstall ubuntu! =)

also, can you answer question 3 for me?

3) If the net-responsibility-daemon is running will it appear in the process list of the task monitor?

i'm just trying to make sure it's all working correctly.

thanks! Hi Nicodemus144
> 3) If the net-responsibility-daemon is running will it appear in the process list of the task monitor?The Net Responsibility daemon runs under ruby, so look for a ruby process in the system monitor. If you place your pointer over ruby the tooltip will give you more information confirming that it is the Net Responsibility daemon.

---

### Post by mpnordland on 2010-11-11
> 

also, can you answer question 3 for me?

3) If the net-responsibility-daemon is running will it appear in the process list of the task monitor?

i'm just trying to make sure it's all working correctly.

thanks!
The daemon won't show up, but you can see if it is working by typing ```
sudo net-responsibility-report --testmail
```
and then check your email inbox. Also, you'll need to register a free account on the website as well if you haven't done so already.
Micah

---

### Post by mpnordland on 2010-11-11
@teltralectic
The daemon won't show up as it is run with the "root" user. gnome-system-monitor only shows the processes running in your user.

---

### Post by Nicodemus144 on 2010-11-11
ok, so i ran the testmail command and i do not receive a report.
here's what it returns in the terminal


spatane@Zephyr:~$ sudo net-responsibility-report --testmail
[sudo] password for spatane: 
Downloading the configurationfile...
Loading it.
/usr/share/net-responsibility/lib/options.rb:227:in `update_settings': undefined method `each_with_index' for nil:NilClass (NoMethodError)
	from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
	from /usr/local/bin/net-responsibility-report:77:in `new'
	from /usr/local/bin/net-responsibility-report:77:in `initialize'
	from /usr/local/bin/net-responsibility-report:134:in `new'
	from /usr/local/bin/net-responsibility-report:134


any thoughts?  i'm getting this same error on two different machines.  one is 64-bit, the other 32-bit.

---

### Post by mpnordland on 2010-11-12
Alright, now we need roggan87 He's the guy who works on that. I'll email him about this.

---

### Post by roggan87 on 2010-11-12
> **Nicodemus144 said:**
> ok, so i ran the testmail command and i do not receive a report.
here's what it returns in the terminal


spatane@Zephyr:~$ sudo net-responsibility-report --testmail
[sudo] password for spatane: 
Downloading the configurationfile...
Loading it.
/usr/share/net-responsibility/lib/options.rb:227:in `update_settings': undefined method `each_with_index' for nil:NilClass (NoMethodError)
	from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
	from /usr/local/bin/net-responsibility-report:77:in `new'
	from /usr/local/bin/net-responsibility-report:77:in `initialize'
	from /usr/local/bin/net-responsibility-report:134:in `new'
	from /usr/local/bin/net-responsibility-report:134


any thoughts?  i'm getting this same error on two different machines.  one is 64-bit, the other 32-bit.

Alright, glad you could manage to install 2.0a3!
Regarding if the daemon is running, see this post: [http://netresponsibility.com/help.php#84](http://netresponsibility.com/help.php#84)

You need to use at least one blacklist in order to get the report to work. Alternatively you can choose to not include the report part called warnings, but you still need to choose at least one blacklist, otherwise the problem will still occur. Let us know if you get it working, or need more guidance.
Good luck!

---

### Post by tetralectic on 2010-11-12
> **mpnordland said:**
> @teltralectic
The daemon won't show up as it is run with the "root" user. gnome-system-monitor only shows the processes running in your user.Hi mpnorland

Actually there's an option in gnome-system-monitor to list all processes (and that includes root owned processes), not just the users. I forgot to mention that the list all processes option has to be enabled.

I really appreciate what you and roggan87 are doing with Net Responsibility

Many Thanks

tetralectic

---

### Post by mpnordland on 2010-11-12
Ahh, I did not know that, I expected such a thing to be like a check box at the bottom of the window, but I found it in the "View" menu.

---

### Post by Nicodemus144 on 2010-11-12
ok great! thanks a bunch for everyone's help!

it is generating reports now.  sometimes i still get a similar error, but other times it just works.

now i set the auto report to 1 day to see if it will auto generate correctly.

thanks tetra for that hint! i was able to confirm that the daemon is running with that easy method.

a word about the attached report option: when i try to just view the attachment, which i just use to list the hostnames i've visited, it tells me that Javascript isn't enabled, even though it is.  i have to actually download the attachment and then open it in order for it to work.

suggestion: i'd love an option to add Only Hostnames or Complete History to the Report parts section to be included in the email, as opposed to just the expanded Attached report.  the example report indicates that NR can do this, but i can't seem to find the configuration options to make it do so.

[http://www.netresponsibility.com/example_report.htm](http://www.netresponsibility.com/example_report.htm)


thanks so much for all your hard work! Net Responsibility is great and has come a long way! i look forward to seeing it continue to grow!

---

### Post by mpnordland on 2010-11-12
Just a quick question, do you use gmail?

---

### Post by Nicodemus144 on 2010-11-13
> **mpnordland said:**
> Just a quick question, do you use gmail?

indeed i do.

---

### Post by mpnordland on 2010-11-13
me too, When you view it, I think gmail blocks javascript, because then somebody might be able to crack their servers with a javascript attack. You will alway's be able to view the reports once you have downloaded them. I had the same problem as you had.

---

### Post by mpnordland on 2010-11-13
Hurrah for Python! 
Roggan, I have finally gotten the error that is keeping the gui from configuring! here is the error msg:
```
/usr/local/bin/net-responsibility-config-cli:98:in `gets': No such file or directory - a (Errno::ENOENT)
	from /usr/local/bin/net-responsibility-config-cli:98:in `initialize'
	from /usr/local/bin/net-responsibility-config-cli:133:in `new'
	from /usr/local/bin/net-responsibility-config-cli
```
the text from the password field is getting passed to the gets statement, weird, and I don't have any idea why.
Fixed! I needed a space in this line:
old:
config_dialog=ProgressDialog(self, "sudo net-responsibility-config-cli --setusername "+ username+  '--setpassword '+password, "Configuring")
new:                                                                                               
config_dialog=ProgressDialog(self, "sudo net-responsibility-config-cli --setusername "+ username+  ' --setpassword '+password, "Configuring")
Version 2 of the gui is done! I will now upload it for testing.

---

### Post by mpnordland on 2010-11-13
Here it is. Use gksu to test.

---

### Post by roggan87 on 2010-11-14
> **mpnordland said:**
> Here it is. Use gksu to test.

Yeah, now we're talking! This is really something. Some very small things I noticed:
1. The report button is still trying to run dummy_config, so simply replace the command on line 72.
2. I'd like the ProgressDialog a little bigger, so I tried size=(505, 400) and think that's better.
3. In the no_input_message I'd like if it was no space before "Try again".
4. I think the main window could be a little smaller, at least the height of it. Couldn't figure out how to do that though.

As I said, really no big deal, just some small improvements.
I attached a modified version.

---

### Post by mpnordland on 2010-11-14
ok, I can do that, I nuked my kernel yesterday, and I still have to fix grub, I using maverick live cd right now. 
in __init__ of ConfigFrame the line: 
```
 
wx.Frame.__init__(self, None, -1, title=title)

```add a "size" parameter
such as ```
size = (200, 250)
```just add it right after ```
title=title
``` with a comma between them. adjust the second item of the tuple to change the height.

---

### Post by mpnordland on 2010-11-14
grub fixed, back in my ubuntu

---

### Post by mpnordland on 2010-11-15
> **roggan87 said:**
> 
3. In the no_input_message I'd like if it was no space before "Try again".

You mean no new line? because there is no space in front of it on my system.

---

### Post by roggan87 on 2010-11-15
> **mpnordland said:**
> You mean no new line? because there is no space in front of it on my system.

Nice, I tried to change the size of the main window, but I'm not sure yet of how big it should be.

No I mean the space. The new line is good, but at least on my system there is also a space before "Try again", which is the result of the string: "No Username/Password entered.\n Try again.". I replaced it to "No Username/Password entered.\nTry again."
Did you notice the space right after \n?

Just one more thought. I wonder if we should keep or delete the message "Configuration Finished". Optionally we could move it to net-responsbility-config-cli. The message is shown whether the configuration works out fine, or returns an error. It's a little overkill to have it displayed both in the ProgressDialog and the main window.

Other than that, I think it's ready to implement in the new version!

Many thanks for your efforts Micah!

Roggan

---

### Post by mpnordland on 2010-11-15
try size=(350,200)
I found that it looks nice. 
And now that I look at it, your right, there was a space. I removed it. and your right, it does look better.

---

### Post by mpnordland on 2010-11-15
On my setup, In the ProgressDialog, it just says "saving the configuration..." I think we should leave the Configuration Finished message there.

---

### Post by roggan87 on 2010-11-16
> **mpnordland said:**
> On my setup, In the ProgressDialog, it just says "saving the configuration..." I think we should leave the Configuration Finished message there.

350x200 looks good!

Sorry, I was unclear. I mean we could move the text "Configuration Finished" to the ProgressDialog, which means to net-responsibility-config-cli. I'm not sure if it's the same for all, but as for me I have to manually close the ProgressDialog when it's done. That means I have to know the configuration is completed before I close the dialog, and after that there's no point telling me it's finished. The same goes with the testmail and report, there should be something like "The report is sent" at the end.

Also, if I type wrong password or username, or have no Internet connection, the text appears anyway, which makes me wonder; Did it succeed or not?

If I try more than once, the message will put itself underneath the old one, creating multiple "Configuration Finished".

I'm probably ridiculous, but why make this software more confusing than it already is? ;)

Hope you don't take me wrong, I'm impressed by your work, I could never achieve this without you!

---

### Post by mpnordland on 2010-11-16
> Also, if I type wrong password or username, or have no Internet connection, the text appears anyway, which makes me wonder; Did it succeed or not?

If I try more than once, the message will put itself underneath the old one, creating multiple "Configuration Finished".

oh, I noticed that, I have been thinking on how to show the user that it's done, and one idea that I have implemented is that the progress bar at the bottom no longer just bounces back in forth, it is a real progress bar that fills up as it goes along. When the progress bar is full, the process that was running from it is done. And, Yeah, the Configuration finished would be better if it was in the cli. Another thing, May be make the error messages come out a little easier to read, and not so formidable e.g. Could not connect to the Internet instead of the trace and then: SocketError: Could not connect to the internet. I could do this if you would like.

---

### Post by roggan87 on 2010-11-16
> **mpnordland said:**
> oh, I noticed that, I have been thinking on how to show the user that it's done, and one idea that I have implemented is that the progress bar at the bottom no longer just bounces back in forth, it is a real progress bar that fills up as it goes along. When the progress bar is full, the process that was running from it is done. And, Yeah, the Configuration finished would be better if it was in the cli. Another thing, May be make the error messages come out a little easier to read, and not so formidable e.g. Could not connect to the Internet instead of the trace and then: SocketError: Could not connect to the internet. I could do this if you would like.

Ah, I see. I'll add the message to the config-cli. I've also been thinking 
about the error messages. I agree that a more understandable output would be better. I'll put that on the todo list as well.

Take care!

---

### Post by mpnordland on 2010-11-19
roggan87: 
I have done some thinking, and once all the bugs are cleared out of what I think will be called net-responsibility2a4 we need to declare it done, stable and finished. The reason being is that we need to have a stable release so that people who are hesitant to use net-responsibility because of perceived instability and buggy-ness will start using it. The other reason is that we just can't keep on just making new alphas, cause it will start to get ridiculous. I have some proposals for what we should do with this new version, if we go that route, and I will deal with them in a later post.
mpnordland

---

### Post by roggan87 on 2010-11-19
> **mpnordland said:**
> roggan87: 
I have done some thinking, and once all the bugs are cleared out of what I think will be called net-responsibility2a4 we need to declare it done, stable and finished. The reason being is that we need to have a stable release so that people who are hesitant to use net-responsibility because of perceived instability and buggy-ness will start using it. The other reason is that we just can't keep on just making new alphas, cause it will start to get ridiculous. I have some proposals for what we should do with this new version, if we go that route, and I will deal with them in a later post.
mpnordland

Micah, you're 100% right! I've been thinking exactly the same. It's ridiculous with all the alphas, and the versioning have been really weird. When we release the first stable 2.0 we have to correct this issue. I also think this version will be ready for the stable state, after some bug-tests. I couldn't agree with you more.

I have some thoughts on what to implement in the next stable release, like 2.1, but that's a bit further down the road.

Thanks for your great efforts in this project, and these valuable thoughts.
God bless!

---

### Post by sadastronaut on 2010-11-19
I know this isn't a Ubuntu question, but how hard is it to get this to run on OpenSuSE ?
Thanks

---

### Post by mpnordland on 2010-11-19
Feel free to ask questions about other distros. This is about net-responsibility, and is sort of distro agnostic. 
What you should try first is install the rpm from the website.
[http://www.netresponsibility.com/](http://www.netresponsibility.com/)

---

### Post by roggan87 on 2010-11-20
> **sadastronaut said:**
> I know this isn't a Ubuntu question, but how hard is it to get this to run on OpenSuSE ?
Thanks

I shouldn't be too hard. Most of us are running Ubuntu or any other distro that's using the debian package system. That's why there's currently no rpm package for the latest releases. If you want, you can try to create an rpm file from the source. That requires EPM ([www.epmhome.org](www.epmhome.org)). After you've installed EPM, download and unpack the source code, and run the following commands:
```
cd /the_source_code_folder/
sudo ./configure-packages
sudo ./make_rpm.sh
```
If everything works out fine, you should have a new folder containing your fresh rpm.

If it's working, please let us know, so we can upload the rpm to the website.
Thanks!

---

### Post by roggan87 on 2010-11-22
New release!

I've updated the website with a new version. This will be the last alpha before the real stable 2.0 release.

Note that you'll have to update your settings online. Even if you don't change a thing, you still have to log in and save the configuration.

Updates:
[LIST]
[*]Much thanks to Joshua (huzzak) there is now a filtering method called tokenmatch. This means the reports will be more accurate with less false positives. It also means that the reports will take more time to produce. Therefore it will be optional, the old method is default. Perform the tokenmatch either by running the command "sudo net-responsibility-report --tokenmatch" or by checking the checkbox called "Always perform tokenmatch" on the website.
[*]Micah (mpnordland) have upgraded the gui, so there's even better configuration and buttons to send reports and testmails. Shiploads of thanks to you Micah!
[*]The blacklists will be stored locally, and only downloaded if they've been modified, or if it's time to update them.
[*]There's an option called "Provide improvement data", which we'd like to encourage you all to use. That would help us a lot in the process of making the blacklists better.
[*]The reports are a little different, showing a top message and internal links. You'll see what I mean ;)
[*]The code have been polished so it's easier to understand and work with (as developer).
[/LIST]

These updates may not effect all of you, but it's a quite big step in a process towards faster and more accurate reports.

There's also some updates on the website, especially with configuration and registration. Personally I like the Regexp Editor :)

Okay, that's it folks. Please let me know of bugs and stuff. Any feedback is welcome!

Take care,
Roggan

---

### Post by mpnordland on 2010-11-22
I'm going to install right away!

---

### Post by mpnordland on 2010-11-22
just a note, need to update the front page on the website, still says 2.0a3 instead of a4

---

### Post by mpnordland on 2010-11-23
I've made a bit of design change in the gui, I will be splitting it into a main file and various modules that the main file will import. I believe that this will make it easier to extend and maintain. It will also make for cleaner code. Therefore, if any one has an improvement to the gui, don't just append it on to the main file, instead, create a separate file, and import it into wherever it need to be. 
Thanks,Micah
ps. if it is a bug fix, you should just fix the bug where it is.

---

### Post by mpnordland on 2010-11-23
I've attached a screen shot of what the blacklist/white list tab of the gui looks like[ATTACH]176397[/ATTACH]
tell me what you think

---

### Post by roggan87 on 2010-11-26
> **mpnordland said:**
> I've made a bit of design change in the gui, I will be splitting it into a main file and various modules that the main file will import. I believe that this will make it easier to extend and maintain. It will also make for cleaner code. Therefore, if any one has an improvement to the gui, don't just append it on to the main file, instead, create a separate file, and import it into wherever it need to be. 
Thanks,Micah
ps. if it is a bug fix, you should just fix the bug where it is.

Sounds good!
I'd suggest you put the main file in the Net Responsibility "root folder" (/usr/share/net-responsibility/ by default), and all the modules in a subfolder called "gui".

> I've attached a screen shot of what the blacklist/white list tab of the gui looks likeAttachment 176397
tell me what you think

It looks good. I think that the black/whitelist are the hardest part to work with. We want to validate the regexps before they get saved. Please have a look at the Regexp Editor on the website. If they're invalid they might cause problems, but hopefully not. At the same time there's only a few people using this feature yet.

My suggestion (note: not order) is to start with the more simple parts like report frequency, blacklist categories, report parts etc. It would be cool to import existing values from the configuration file like it's done in send_report.py. At the moment /etc/net-responsibility.conf is pretty scaled down, but I can fix that if you'd like.

It's so nice to see the gui taking form! You're doing a great job.

---

### Post by mpnordland on 2010-11-26
> **roggan87 said:**
> Sounds good!
I'd suggest you put the main file in the Net Responsibility "root folder" (/usr/share/net-responsibility/ by default), and all the modules in a subfolder called "gui".



It looks good. I think that the black/whitelist are the hardest part to work with. We want to validate the regexps before they get saved. Please have a look at the Regexp Editor on the website. If they're invalid they might cause problems, but hopefully not. At the same time there's only a few people using this feature yet.

My suggestion (note: not order) is to start with the more simple parts like report frequency, blacklist categories, report parts etc. It would be cool to import existing values from the configuration file like it's done in send_report.py. At the moment /etc/net-responsibility.conf is pretty scaled down, but I can fix that if you'd like.

It's so nice to see the gui taking form! You're doing a great job.

Oh, right now the gui is just a window, some text boxes and buttons ontop of the work you've already done, and its probably a better idea to start with report frequency first. Is that in the .conf file? If so, I'll just write some code to change it my self. If not, tell me where it is! I also want to work on the multiple users on one computer, I have two ideas on how to implement them that are in basic form. 
1. All users have a separate .conf file,
2. each user has a section in one .conf file
Checking for user switching will have to be done by the daemon, and we'll have to figure out a desktop independent way to check for user switching, eg not dependent on say, libgnome-ruby

---

### Post by mpnordland on 2010-11-26
also, I don't understand exactly how to use the Repexp editor, The expresions are clearly explained, but how to use the Regexp editor to add them to your black/white list is not. Also, The "How to Configure" documentation needs to be updated, I will do that, and post it for review in a few days.

---

### Post by DustStuff on 2010-11-29
Hi Everyone! After being off my Linux machine for awhile and finishing a series of upgrades ending in Ubuntu 10.10 I decided to install the latest NR and do any necessary updates to the documentation for the install and configuration, etc. Didn't get as far as I wanted because I was distracted for a few too many hours by an apparent suicide attempt by Thunderbird, but here's a report on the install, including an error received when trying to send a manual report:

System: Ubuntu 10.10 (upgraded from 10.04 rather than a clean install)
Last NR Version: I think it was 2.0a1 on Ubuntu 9.10

--Downloaded .deb file from website, and double-clicked on it, which opened Ubuntu Software Center.
--Clicked on 'Upgrade' ('upgrade' because it recognized there was already a version installed). Took a bit of time, but seemed to install fine.
--Had no trouble finding the menu item for configuration in the same two places it had been previously, and it worked fine to get to the GUI (in my case, clicking on the menu item simply triggered an authentication box where I could enter my password and then move on to the GUI; this is default behavior in Ubuntu 10.10 and I'm pretty sure it was in 9.10 as well).
--Typed in user name and password and clicked on 'Configure', which brought up the corresponding window. (BTW, I like the idea of some sort of movement on the progress bar while things are happening, since on my machine it looked like there was just a blank window and I wasn't sure anything was happening until I started seeing some output. Part of the reason for this was also the lack of contrast between the progress bar background and the window background, which made it hard for me to tell that there was a progress bar, until at the end when it filled up with the color.)
--Clicked on the 'Test Mail' button, which worked fine and I got the test email in my inbox fairly quickly. (One question: Is the test email supposed to have an attachment on it? The reason I ask is because in my Thunderbird, it shows it having an attachment when it is in its unread state, but as soon as you click on it to open or preview the attachment icon [paper clip] disappears. Not a big deal with this, but if it happens with attached reports, that would be an issue.
--Clicked on 'Report' button. Eventually received what I would assume is normal output ending with 'Report Finished', but then also received the following error message:
```
/usr/share/net-responsibility/lib/report.rb:212:in `+': can't convert nil into Array (TypeError)
    from /usr/share/net-responsibility/lib/report.rb:212:in `full_report'
    from /usr/local/bin/net-responsibility-report:89:in `initialize'
    from /usr/local/bin/net-responsibility-report:134:in `new'
    from /usr/local/bin/net-responsibility-report:134
```
--Not only did I get the above error, but also I did not receive a report in my email inbox.
--Thought this might have been from not having any internet activity, so surfed a bit before trying again, but same result. Also tried logging in on website and logging out (with save, but no changes), running Config again, surfing, and then trying 'Report' button again, but got the same error. Checked Synaptic, CLI version command, and CLI 'is the daemon running?' tests to make sure NR was running. Also ran the CLI 'manual report' command and got the same error as above in the terminal. Used Synaptic to do a 'Complete Removal' of NR and then installed it again in the same way as above. I followed this with logging in and out of the website without making any changes, running Config again, doing a test email again which worked fine, and then tried the 'Report' button again. But got the same error, and double-checked that it was giving the same error in the terminal as well when trying the CLI 'manual report' command.
--Logged in again to website and made a few changes, including the reporting frequency from '7' to '1' so I can test automatic reporting (I'm assuming it will work, but will let you know if it doesn't.)

So, not sure if anyone else has encountered this error related to doing a manual report, but I thought I should mention it, and thought I'd also include the install process of this latest NR on Ubuntu 10.10. Feel free to let me know if you have any questions.

---

### Post by mpnordland on 2010-11-30
automatic reporting will work, and make sure that you have at least one blacklist selected, and you should also add at least one item to your personal whitelist. The whitelist bug should have been fixed, but maybe we missed something. If it still goes wrong, you should check with roggan87.
ps, Thanks for working on the docs

---

### Post by roggan87 on 2010-11-30
Okay, I'll try to quickly answer some questions here :)

I like the idea with mutliuser support. I've looked a bit at it myself, but hope that you might get further! I think multiple .conf files would be the best. The part that I didn't really figure out was how to determine which user was running, since the program is run by root. Usually you use the commmand "whoami", but "sudo whoami" will just output "root". If there's another command, or method, that can tell us who is actually running, then it'll be possible to proceed. The best command I found was "hostname", but I'm not really sure if that's a good idea to use.

Sorry about the documentation on the Regexp Editor. Haven't had time to write it, but I understand the need. I'll try to write a simple tutorial on how to use it.

Dustin, good to have you back! I've fixed the bug, I hope. Try downloading 2.0a4 again and reinstall. I'm not sure what might cause the problem you mentioned on the admin pages. I've done some work there, and hope that we can use TinyMCE to edit the texts. It's working for me. Check it out on this page ([http://tinymce.moxiecode.com/](http://tinymce.moxiecode.com/)) and see if it seems to work there. Otherwise that might be it.

So, thanks for your efforts guys!
God bless,
Roggan

---

### Post by mpnordland on 2010-11-30
I've asked a question on comp.lang.python, I don't know if we want to do this in ruby or python, if this needs to be ruby, I will learn!

---

### Post by DustStuff on 2010-12-01
Thanks, mpnordland and roggan87, for your suggestions and the bug fix. Here's an update on the various issues I've been facing:

In regards to the NR install, once I downloaded the new install file from the website and installed it (after doing a complete removal of the previous one), I was able to run a few of the tests mentioned before to make sure things are working, including the manual report, both from the GUI and the CLI. As expected, these gave basically the same output, and didn't include the error I had mentioned earlier. One (possibly ongoing) issue is that both of these manual reports ended up in my Gmail spam folder, rather than making it through to Thunderbird on my machine. I logged into Gmail to let it know that these were not spam and then retrieved them my usual way via POP3 and TB. Now, I dont know for sure why they were triggered as spam, since other emails from the same address had been making it through. Also, the testmail I ran after this latest install made it through fine. My guess is that it is either because these reports were sent manually, or maybe more likely, because they contained attachments with javascript (JS) in them (this is the first that I've had this type of report delivered). I'm still waiting to make sure the automatic reporting works (which I assume it will) and to see if it makes it past Gmail's spam folder (I assume it will, since I flagged the other reports as 'not spam'). My previous test of the automatic reporting didn't work because I must not have saved my changes the last time, which included changing my frequency from '7' to '1'. So, I'm pretty confident that my install is pretty much worked out and things are running as they should -- we'll see.

In regards to the reports, I like the way they are taking shape, but I have a few comments and questions that may serve as helpful information/feedback or may help you shed some light on some of my ongoing issues:
--I'm getting the message in Thunderbird (3.1.6) (in the inline attachment of the report) that JavaScript is not enabled. It seems unlikely to me that Gmail could enforce a no-JS policy within my email client, so I'm guessing that JS is not enabled in TB or it's not working for some reason. I clicked on the link for 'Show Remote Content' but it still gives the same JS error. Also, there does not seem to be any way to enable JS in TB through the normal preferences -- there may be through the Config Editor, but I decided not to get into that. At one point I also wondered whether TB would just default to whatever settings I was using for Firefox (3.6.12), but that was not the case either.
--BTW, in my attempts to figure out if I had a problem, what it was, and how to fix it, I ended up installing both Java and JavaScript, as well as using a couple online tests with FF to make sure they were working. Not sure if I would have needed to (I think I may have needed at least JavaScript, unless it was installed before without me realizing it), but they are both installed, enabled and working with FF.
--Double-clicking the attached report opens up a tab in FF, as one would expect, and it does not give any message about JS not being enabled, etc., so I take that as a good sign.
--Even though the report opens in FF, it doesn't behave in the way I would expect it to. Both of the JS links to the right of 'Options' work when you click on them, although if you have the nodes extended and you click on the 'Hide/Display Time' link it collapses all the nodes again. But none of the lower links seem to work when you click on them (I'm assuming they are supposed to extend the nodes of their particular subsection, similar to how that section would look when all the nodes are extended). When I hover over them, they all have 'javascript:_foo()' as their 'link'. If that's how they're supposed to be, that's fine -- it just seemed odd to me. Because basically, at this point, if I want to look at the info under any of those links, I have to click on 'Extend all nodes', which could potentially take awhile and would provide a boatload of information, possibly more than an accountability partner would want or need. Anyway, those are a few of my observations on the reports, in case they are helpful.

My main ongoing problem at the moment is that I haven't been able to figure out how to edit the documentation on the website. Basically, I can log in and edit things, but I can't get the 'Update' or 'Add' button to do anything to actually make the changes. Here's a few ideas I thought of:
--Thought it might be because Java or JavaScript weren't installed, but didn't change once they were.
--Thought it might be a problem with FF's AdBlock Plus extension, so I disabled it, restarted FF and tried again. Didn't work.
--Thought it might be FF, so I tried Chromium (a fresh install without anything other than its necessary dependencies installed). Didn't work.
--Wasn't sure exactly how to check this on the TinyMCE site, but I went to the 'Example' page and was able to type a line of bold text and click the 'Submit' button, and everything seemed to work fine. So, that seemed to work okay in FF.
--Is it possible that FF and Chromium have some sort of built-in security features that need to be accounted for in the code somehow? The reason I ask is because in the TinyMCE forums there was an example of someone who was trying to copy and paste some code in later versions of both FF (and I think Chrome/Chromium), and it would automatically delete parts of the code because it didn't want certain scripts to run, etc.
--Also, Roggan, could you tell me what browser and version you are using in order to get this to work? If it is different than the ones I tried, then it may mean it's a browser issue, but also it may mean that I can download that particular browser and version and get it to work.
--This might be a dumb question, :) but do I need to have TinyMCE installed on my machine for this to work? If that's all it takes, I should be able to do that easy enough.

Well, I think that's all I have for now. Any light anyone can shed on these things, especially the last one, would be appreciated. Thanks! And I appreciate all the work you other guys are doing. :)

---

### Post by roggan87 on 2010-12-01
Glad you managed to install NR Dustin :)

Not sure about the spam error. I remember having problems with Gmail. Especially if I tried to send multiple identical emails, such as the testmails. Maybe one can ask the same question at a Gmail forum?

The JavaScript error is already known. The problem is that JavaScript might include harmful code, and therefore some email providers (such as Gmail) and email clients (such as Thunderbird) choose to remove all JavaScript code from the emails. The workaround is to open the attachment in a browser. Sometimes you have the possibility to download or open the file directly, in that case direct open won't work, but download and open will work. In Firefox you should click download, and then you can decide to open in Firefox or save to computer. At that stage you can open in Firefox. Hope all this makes some sense :) We would definitely need better info for this on the website. I think we would need a whole category for accountability partner usage info.

The attached report should work better now. I apologize for the bug, good you mentioned! The "javascript:_foo()" is no bug, but I agree, I'd also like it to open the node. Instead the "+" to the left opens the node.

I don't really understand why you can't edit the texts. Please try to click the link "Show/hide HTML code" and see if that works. I'm using Kubuntu 10.04 and Firefox 3.6.9. TimyMCE seems to work on your computer, and you don't have to install it.

Good luck and let me know of any progress!

---

### Post by roggan87 on 2010-12-01
Micah,

I've added an article on how to use the Regexp Editor here: [http://www.netresponsibility.com/article.php?id=109](http://www.netresponsibility.com/article.php?id=109)

It's only for regular users, and not admins. As admin one can also edit the existing blacklists here.

Be blessed :)

---

### Post by mpnordland on 2010-12-01
Ok, that clears things up for me immensely.
And, in python, with the os module, we can start a script as root, but in said script change to be owned by a normal user, then we can run whoami, write and send a msg back to the daemon

---

### Post by mpnordland on 2010-12-01
and what is the difference between admin and regular user in this case?

---

### Post by mpnordland on 2010-12-01
I have started the gui configuration how to, and I have attached it for review. Please feel free to point out errors, it will make it better.
roggan, i think that we'll do per-user .confs and name them like this: user-NR.conf That should keep our typing to a min, and will be easy to make the program name them. the user part should be the username of the computer their on, and not their net-responsibility username.
also, we can use dbus to send msg from a whoami script to nr daemon, daemon gets msg and takes appropriate action. The whoami script would run at login. I don't know what to do for user switching without logging out and someone else logging in.

---

### Post by logon68 on 2010-12-02
[***i  agree with ***]("http://ubuntuforums.org/member.php?u=323618")[raijinsetsu]("http://ubuntuforums.org/member.php?u=323618")

---

### Post by Cityscape on 2010-12-02
We were configuring Net Responsibility today and put in a wrong username/password.

So when we put in our correct username/password we got this error:
> /usr/local/bin/net-responsibility-config-cli:114:in `initialize': ERROR (RuntimeError)
Another account have already been set up on your computer. Please delete that account before you use this one.
from /usr/local/bin/net-responsibility-config-cli:132:in `new'
from /usr/local/bin/net-responsibility-config-cli:132
How can we remove this account that has been set up so we can setup the proper account?

---

### Post by mpnordland on 2010-12-02
> **logon68 said:**
> [***i  agree with ***]("http://ubuntuforums.org/member.php?u=323618")[raijinsetsu]("http://ubuntuforums.org/member.php?u=323618")

About what?

---

### Post by mpnordland on 2010-12-02
> **Cityscape said:**
> We were configuring Net Responsibility today and put in a wrong username/password.

So when we put in our correct username/password we got this error:

How can we remove this account that has been set up so we can setup the proper account?
Did you get the password wrong or the username?

---

### Post by Cityscape on 2010-12-02
> **mpnordland said:**
> Did you get the password wrong or the username?
We don't actually know. We may have got just one of them wrong or maybe even both wrong.

We just want to erase this other account that has been "set up" so we can input our correct information. ???

---

### Post by roggan87 on 2010-12-03
I like the idea to run a script that sends a message back to the daemon.

The configuration howto looks nice. The only thing I thought about is the last sentence, where it says that the message "Configuration Finished" is a confirmation that Net Responsibility is set up properly. At least on my computer, that message appears even if the configuration fails. In the ProgressDialog it's only shown on success, but in the main window it's displayed every time. That's why I thought we maybe should skip the last message.

> We were configuring Net Responsibility today and put in a wrong username/password.

So when we put in our correct username/password we got this error:
Quote:
/usr/local/bin/net-responsibility-config-cli:114:in `initialize': ERROR (RuntimeError)
Another account have already been set up on your computer. Please delete that account before you use this one.
from /usr/local/bin/net-responsibility-config-cli:132:in `new'
from /usr/local/bin/net-responsibility-config-cli:132
How can we remove this account that has been set up so we can setup the proper account? 

This error message means that you've installed Net Responsibility with another account earlier on the same computer. The reason it'll stop you from setting up the computer with another account is because that would open up the possibility to run several accounts and switch between them, without letting the accountability partner know. Now you have to delete the old account before you can start using a new, and the accountability partner is getting an email about this. If you haven't used another account, this might be a bug. In that case it would be useful to know your MAC address. You can get it by running this command:
```
ifconfig -a | grep HWaddr | cut -c39-
```

Good luck :)

---

### Post by DustStuff on 2010-12-03
@roggan87 -- If cityscape's priority is to get NR up and running on their computer, would it work to do a complete removal of NR and then install it again? Or would that not clear the info that's potentially causing this error message? If it is a bug, though, it's good that we're finding it now, I guess. :)

---

### Post by DustStuff on 2010-12-03
Thanks, Robert, for your time and help with these various things!

On the spam thing, I think I'll just make sure this (the possibility of checking if missing reports were quarantined) gets included somewhere in the documentation (I'm going to try to follow your suggestion that you also mentioned awhile back about making it a priority to get some stuff up for accountability partners), since that end of things (mail servers' spam filters) is sort of out of our hands and is probably continually being adjusted.

Your explanation on the JavaScript thing was quite helpful -- my basic mistake was assuming a 'direct open' from TB would be the same as downloading to my PC and then opening in FF. So once I opened it outside of TB, it worked no problem, and I am quite impressed with the options the tree structure gives you -- definitely worth the time you (and/or other developers) put into it in my opinion. The only little quirks left are needing to use the +/- symbols for opening the tree rather than also having the option to use the links, and the way that the time display link collapses any node that is open when it's clicked. But these are both small things in my opinion, which I can make sure get included in the documentation until they're no longer needed. BTW, I'm also toying with the idea of putting some of the most basic report-related help info right into the report itself, and maybe even a more-specific link to the accountability-partner-related doc(s) on the website, once those are up. I don't know how hard it is to put stuff right into the reports, or whether there's a way for me to do that myself, or whether I need to send it to you. Whatever the case, I'll check things out, and email you if I need assistance or have any proposed changes.

Okay, on the website editing front, I've been having lots of 'fun'. :) Not much real progress (that I'm aware of), but here is some more info I'll throw out there, in case it might lead to some sort of solution:

--Background from previous post: Latest versions of Chromium browser and FF (3.6.12) were tried on an Ubuntu 10.10 machine with no sucess.
--In answer to your question, the HTML toggle link worked fine for me; it seems the only thing I haven't been able to get to work is that one button that sometimes says 'Update' and sometimes says 'Add' on it.
--Tried FF 3.6.12 on my Toshiba netbook, which is running WinXP. Same problem. Tried IE 8 on the netbook. Same problem. But interestingly, IE 8 mentioned an error on the page that I arrived at after clicking on an 'edit' link (tried this with one or two other pages' 'edit' links and it also gave an error for those). Then, when I clicked on the update button, it mentioned again that there was an 'error on the page'. I checked it out, and IE 8 has a place you can view errors and copy them out, etc. I have no idea if it's relevant in this case, but if you're interested, I can send you more details if you want. Just let me know, and also mention whether you'd prefer them here, in a PM, or by email, since I don't want to get too far OT in this forum. I found it interesting that IE 8 mentioned an error, whereas the other couple browsers I tried didn't give any kind of message, but I guess that's just a difference in browsers.
--Next, I uninstalled FF 3.6.12 from my netbook, restarted, and installed 3.6.9 (your version) in case the version was the issue. I really expected it to work, but still got the same problem.
--Moved back to my Ubuntu 10.10 machine, uninstalled FF 3.6.12, and tried 3.6.9. Same problem.
--Moved to a third machine running a 'minimal install' of (X)ubuntu 9.04, and tried with a Gnome-related browser called 'Web Browser', version 2.26.1 (powered by gecko-1.9). Same problem.
--Thought it might be something related to my internet connection (landline coming into a modem, and run through a router), even though it seems a bit far-fetched. So, I went back to my netbook and tried a USB modem connection with the same FF 3.6.9 and IE 8 browsers. Same problem and same results.

Based on the above information, here are a few comments/questions that can hopefully help in arriving at a solution:
--It seems that this is not something related to a particular browser, version, operating system, or type of internet connection, although I guess there is still a chance it is.
--Do you know if this button works for anyone other than yourself? Related to this, are you able to test whether it works from a different machine than you are doing your current work on?
--Do you think the errors generated when using IE 8 would be helpful at all? I mentioned this above as well, and I'd be happy to send that info to you.
--This might be comparing apples to oranges, but I know the 'Log In' button works fine for me, so would it be helpful to compare the HTML code of that button to this button to see what differences there might be?
--In case it helps, the detailed symptoms are as follows: I can get to the edit page, click inside the frame, and make whatever changes I want, but when I click on the 'Update' button, it gives the normal visual of a button being clicked, but nothing happens, and nothing is generated in the status bar in the lower left corner (except in the case of IE 8 where it just reminds you of there being an error on the page).
--Is there a chance that there is some sort of 'permissions' issue involved where you and your machine are somehow authorized to click on that button and my machine is not? Sounds a bit far-fetched, but I thought I'd throw it out there. :)
--I thought I might be able to find a workaround, but the only one I can think of at this point is to send any edits I have to you or someone else who can do the edits, but it would be nice if you and/or other developers focusing on other things wouldn't have to bother with that.

Well, that's pretty much all the info and ideas I have at this point. Let me know if they triggered any ideas on your end. Thanks!

---

### Post by DustStuff on 2010-12-03
Micah, I checked out your config how-to and I wanted to thank you for posting it! I downloaded it, and added a proposed edit to it, and am attaching the file again with this post. The edit is based on the previous config documentation for 2.0a1, but I think I've made all the necessary changes for 2.0a4. Maybe you and Robert could take a look at my proposed edit to see what you think. It is a bit long, and there's probably a couple ways I could shorten it by dividing out some of the sections, but for now I think it serves the purpose.

If you guys think it looks okay, then the next step is to get it posted on the website. Unfortunately, I'm still unable to make edits. Robert, I don't know if Micah or anyone else is able to make edits, but would you be able to find a way to replace the 2.0a1 documentation with this updated version? Whoever does it, here are the key things to remember:
1. Make sure you don't replace/delete the last little section of the current documentation that deals with v0.5 configuration. :)
2. Make sure that the few places where terminal commands are given are in italics (which I assume is still the convention we're using). I noticed that when I copied and pasted into this attached text file that it lost those italics.
3. I don't think that there was anything else lost in the copy/paste I did, but it might be worth comparing the current documentation with the updated version so that roughly the same layout and formatting shows up.

I'm fine with you guys running with this from here, as my hands are a bit tied. :) If you want, you can let me know once it's been posted, and I can take a look to see how it appears to the average website user.

Thanks to you guys for all the programming stuff you're working on, and I hope this won't take up too much of your valuable time! :)

---

### Post by roggan87 on 2010-12-03
Dustin,

Thanks for very helpful feedback, you've really tried it all. It has to be a server related problem. I found a bug on the page and fixed it, and maybe it's working for you now. I find it strange though that it would work for me, but not for you...

I really wish I could help you get going, since that would help me a lot! You can email me the outputs from IE 8 if you still don't get it working, my email address is: robertrosman [at] gmx [dot] com.

Unfortunately it wouldn't help wiping out the previous install for cityscape, since it's not a client related problem, but a server related.

So, short answers for long questions ;) I really hope this'll do it.

Blessings

---

### Post by DustStuff on 2010-12-03
Robert, thanks much for your prompt reply and your time spent in helping me out with this. Whatever bug you fixed seems to have fixed my problem with being able to edit the website docs, so that is great news! :) And TinyMCE definitely makes it easier to create and edit stuff, so I'm glad you've brought that onboard. I went ahead and updated the config doc I referred to in my last post, so you guys don't need to worry about that, but you can still feel free to check it out and let me know of any suggested changes. No problem for the short answers -- looks like I'm running out of questions for now, so I guess I'll be able to keep this short as well. ;)

---

### Post by mpnordland on 2010-12-06
Wow Dustin! You've been given the gift of documentation! I think that your edit is great. You definitely improved on my little how to, but one thing, there is a command to open the gui, it is: net-responsibility-gui you could change the doc around so that you have two sections, one for the gui, and one for the cli.
Robert, the other idea I had for finding the current user was to use a logon script that sends a msg to the daemon with the current user via dbus. both ruby and python have dbus bindings, and I am currently learning ruby, so in time I could create this.

---

### Post by roggan87 on 2010-12-06
> **mpnordland said:**
> Robert, the other idea I had for finding the current user was to use a logon script that sends a msg to the daemon with the current user via dbus. both ruby and python have dbus bindings, and I am currently learning ruby, so in time I could create this.

Sounds good to me! I don't know much about dbus, but as long as it can help us, I'm happy :) I'm glad you want to dive into this feature, as I think it would improve Net Responsbility a lot. Best wishes!

---

### Post by timaber55 on 2010-12-06
Hi,
I really like net responsibility, and it has worked faultlessly for a while. But recently after updating the version to the latest release, it has stopped sending reports. I have configured it correctly, and I can send test mails via command line. If I try to send a report via command line, it says it works, but it doesnt.
Help!

---

### Post by DustStuff on 2010-12-06
Thanks for the feedback on the config settings doc, Micah! I've made a note of the things you mentioned, and will use those in my next edit of that text.

@timaber55 -- My first thought would be to check and make sure that your email server or email client is not treating the reports as spam, possibly because the newer version's reports have been modified. For instance, when I upgraded I had a similar problem with my Gmail account that I download into Thunderbird. Once I logged into Gmail through my web browser, I found the report in my 'Spam' (could be 'Junk' or 'Trash' too, depending on your email server) folder and clicked on the button to tell Gmail it wasn't spam. Since then, I haven't had any trouble. Also, if you do figure out this is the problem, you may want to mention it to anyone else who is supposed to receive these reports, in case they have a similar problem.

---

### Post by roggan87 on 2010-12-07
> **timaber55 said:**
> Hi,
I really like net responsibility, and it has worked faultlessly for a while. But recently after updating the version to the latest release, it has stopped sending reports. I have configured it correctly, and I can send test mails via command line. If I try to send a report via command line, it says it works, but it doesnt.
Help!

Hi!

What's your output in the terminal when you type this command:

```
sudo net-responsibility-report
```

Would be helpful to know.

Roggan

---

### Post by DustStuff on 2010-12-09
I've made the following updates to the documentation on the website:

--The section on configuration settings in the User Guide was divided out into three sections, one for configuration using the GUI, one for configuration using the CLI, and one showing some ways a user can test whether NR is working properly.

--I've added an [Accountability Partner Guide]("http://www.netresponsibility.com/help.php#117") as a separate section. You may want to let your accountability partners know about this (there's a link to it at the bottom of NR's home page) in case they would find it helpful. Robert, I'm wondering whether it might not be helpful to include a similar link in the reports themselves, titled 'Help' or 'Accountability Partner Guide' or something like that. As far as I can tell, I don't think I can currently do any edits to the text in the reports, so I'll leave that up to you if you think it's a good idea.

Also, whether you're a developer, user, or accountability partner, feel free to check out these various documents and respond with any feedback you have on how they could be made more clear, useful, and accurate. Thanks!

---

### Post by mpnordland on 2010-12-09
Update from the mad programmer (mad as in crazy)
I have started on the multiusers, and i am using a separate script to work out the details, and then, when I've got those done, Robert, I'll need your help for integrating it. May God make it work!!

---

### Post by roggan87 on 2010-12-10
> **mpnordland said:**
> Update from the mad programmer (mad as in crazy)
I have started on the multiusers, and i am using a separate script to work out the details, and then, when I've got those done, Robert, I'll need your help for integrating it. May God make it work!!

Nice!

You've got my thoughts spinning :) I'll try to assist as much as possible. I think highest priority is to release the stable version as soon as possible. But go ahead and do the coding, so we can implement this in the next release.

---

### Post by mpnordland on 2010-12-10
yeah, the stable version is higher priority, and this will take me some time, I've pretty much got the syntax down, just that python doesn't have "end".

---

### Post by tetralectic on 2010-12-10
I just wanted to say that you guys are awesome  --- thanks

:D

---

### Post by roggan87 on 2010-12-11
Micah, you'll get it quick, it's pretty simple ;)

Martin, thanks, appreciate it a lot.

Sorry, I couldn't resist, or actually I sat on a Win-computer and couldn't work on the stable release, so I started to look at the multiuser feature.

I haven't fully tested this command, but it seems to work inside Net Responsibility:
```
user = `echo $SUDO_USER`.chomp
```

When I try the command right in the terminal, "sudo echo $SUDO_USER", I just get an empty line as return value. If I write a very simple script, only including the command, and run it with sudo, it works.

So, you might want to try it out a bit and tweak it around. I think it would be the easiest way to find out which user who started the program.

The man page for sudo says:
> SUDO_USER - Set to the login of the user who invoked sudo

I'll be back,
Robert

---

### Post by mpnordland on 2010-12-13
> The problem is that multiple users can be logged on at the same time.  You might be able to come up with a solution that works for a small set of use-cases, but I admin several Linux boxes where multiple people can be logged-in at the same time.  There are also some multi-head arrangements (multiple keyboards/mice/monitors and sometimes even sound-cards attached to the same motherboard) and people can log into each "terminal" (if you will) concurrently, all on the same box.  So if I'm using the computer, and a co-worker logs in, I'm still using it at the same time you might catch the "new user logged in" event.

Watching wtmp (or possibly /var/log/auth) can capture the "hey, somebody logged in" event, but that doesn't mean that other previous users are done with their sessions.

this is from the comp.lang.python list and it raises an important issue, the fact that there could be more than one user actively using the system at any given point. Some how, if we could just get the process id's from all running browsers, and get the user id's from the process, then we could just record the urls from each user to the log file for that user. As for that command, I'm not sure if it will work or not. The daemon is started at boot, and I don't think that it is started by any one user.

---

### Post by roggan87 on 2010-12-13
> **mpnordland said:**
> this is from the comp.lang.python list and it raises an important issue, the fact that there could be more than one user actively using the system at any given point. Some how, if we could just get the process id's from all running browsers, and get the user id's from the process, then we could just record the urls from each user to the log file for that user. As for that command, I'm not sure if it will work or not. The daemon is started at boot, and I don't think that it is started by any one user.

Oh, I haven't thought of Net Responsibility being started at boot time. You're right that command didn't work out as I thought.

I just found out that urlsnarf, the program that listens on visited URLs, is actually giving us the user who tried to reach each site. That is useful info, I haven't seen that before. You can try yourself with this command:
> sudo urlsnarf -i all

Maybe one solution would be to save one config file each, one log file each etc., and use the right settings depending on the urlsnarf output. We always write the config files in net-responsibility-config-cli, and that program isn't started at boot time, so SUDO_USER might be useful here.

By the way, I've uploaded the stable release of 2.0 on the website. I haven't done any official release, and this is not it. I'd like you guys to try it out first, just in case. There are some very minor fixes compared to 2.0a4. Let me know if it works as expected, or not. Here are the files:
[http://netresponsibility.com/files/netresponsibility-2.0.deb](http://netresponsibility.com/files/netresponsibility-2.0.deb)
[http://netresponsibility.com/files/netresponsibility-2.0.amd64.deb](http://netresponsibility.com/files/netresponsibility-2.0.amd64.deb)
[http://netresponsibility.com/files/net-responsibility-2.0.tar.gz](http://netresponsibility.com/files/net-responsibility-2.0.tar.gz)

Best wishes,
Robert

---

### Post by timaber55 on 2010-12-13
roggan87 sorry for the late reply. If i type that command into terminal i get-

> Downloading the configurationfile...
Saving it.
net-responsibility-report[12261]: Generating report
Looking for bad keywords in the hostnames:
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------^Cnet-responsibility-report[12261]: Time for this report: 64.489136
net-responsibility-report[12261]: 
net-responsibility-report[12261]: Report Finished.
/usr/share/net-responsibility/lib/filter.rb:78:in `list_match': Interrupt
    from /usr/share/net-responsibility/lib/filter.rb:76:in `times'
    from /usr/share/net-responsibility/lib/filter.rb:76:in `list_match'
    from /usr/share/net-responsibility/lib/filter.rb:74:in `each'
    from /usr/share/net-responsibility/lib/filter.rb:74:in `list_match'
    from /usr/share/net-responsibility/lib/filter.rb:73:in `each_pair'
    from /usr/share/net-responsibility/lib/filter.rb:73:in `list_match'
    from /usr/share/net-responsibility/lib/filter.rb:58:in `url_match'
    from /usr/share/net-responsibility/lib/report.rb:60:in `warning_report'
    from /usr/share/net-responsibility/lib/report.rb:59:in `each'
    from /usr/share/net-responsibility/lib/report.rb:59:in `warning_report'
    from /usr/share/net-responsibility/lib/report.rb:214:in `full_report'
    from /usr/local/bin/net-responsibility-report:89:in `initialize'
    from /usr/local/bin/net-responsibility-report:134:in `new'
    from /usr/local/bin/net-responsibility-report:134

But no report arrives... not even in the spam folder. Im using google mail and thats recieveing fine. 

I read somewhere that net responsibility accounts that were used with previous releases need modifying to work with the latest release, is this right or am i reading junk (perfectly possible)?

Thanks

---

### Post by mpnordland on 2010-12-13
@timaber55
That's true, did you setup the account before version 2.0a4 was released?
@roggan87
urlsnarf is just giving us the host name, not the user name. maybe it was there, and I missed it, but I couldn't find it. On another note, I am going to start building and testing the rpm version on opensuse, so we can have those back on the website.

---

### Post by DustStuff on 2010-12-13
@timaber55
Have you tried going to the Net Responsibility website, logging in, and then saving and logging out (even if you don't make any changes)? I seem to remember a comment with one of the versions that came out that people would need to do this. If you haven't done that, try it once, and see if that gets things working.

@roggan87
I did the following basic testing of the v2.0 32-bit .deb file from the link in your post, on my Ubuntu 10.10 system:

1. Attempted an update by simply double-clicking on the file. This brought up 'Ubuntu Software Center' (USC) which did not give me the option of installing, giving the message "A later version is already installed." So I don't know if we're running into some of the same problems with systems having version confusion that mssever faced when he was still involved or not. I don't know what the current intent or priority is in relation to people being able to upgrade rather than just install, but I thought I'd at least mention that. For now, an easy work-around is to just uninstall the old version and install the new version.

2. Used Synaptic to uninstall ('Removal') 2.0a4.

3. Repeated step #1, which this time seemed to be successful, although USC mentioned at one place in the window about NR not being available, and another place about this version not being suitable for an i386 computer or something. I assumed that this was probably just the result of me installing something from 'outside' the USC.

4. Did a successful version-check in the terminal.

5. Successfully opened the config GUI via the menu item, and successfully tested each of the three buttons (config, test mail, and manual report). Based on that, I'm assuming automatic reports will work okay as well.

I'll let you know if I happen to run into anything else. Blessings to all of you!

---

### Post by roggan87 on 2010-12-14
@timaber55
What version are you using? You might have to either upgrade, or log in and save settings, as DustStuff mentioned.
The terminal output looks like you've stopped the report process. That might take a while, especially if you're using the tokenmatch. All the lines (-) represents either a hostname or website you've visited. If Net Responsibility think a site is inappropriate it will output (X) instead, and (W) for whitelist match. Please try to run the command without interrupting it, and see if that works. And if you're using the tokenmatch you might want to try the default method to speed up.

@mpnordland
Oh sorry, of course it is. I appreciate that you want to compile the RPMs! Just send them to me when you're done.

@DustStuff
You're right, I forgot to mention. I had the same problem. You need to uninstall the old version first. After this stable release I'm going to name the versions a bit different to avoid this problem. Unstable releases will be called 2.0.1, 2.0.2 etc, and stable releases 2.1, 2.2 etc.

---

### Post by timaber55 on 2010-12-14
Thanks for all the help, I'm running 2.0a4.

@roggan87 I didn't interupt the proccess, not sure why it was doing that. What's tokenmatch?

@DustStuff Thanks I will try that

---

### Post by tetralectic on 2010-12-19
I'm getting an odd problem. I have the option for the complete history to be sent in zipped form checked in my account on the website. When I install/uninstall&reinstall Net Responsibility 2.0 in Ubuntu 10.10 64 bit, the first report sent includes the complete history in a JavaScript tree form as it should. However all in subsequent reports this JavaScript tree does not show up in the attached complete report when opened in Firefox 3.6.13, Chromium 10.0.615.0, Epiphany 2.30.2, or when I virtualize Windows 7 in VirtualBox, in Internet Explorer 8. When I open the report in a text editor such as gedit my history is there in the report file, it just doesn't render when opened in a web browser. This seems to happen whether I'm using the default filtering method or the tokenmatch method. So to recap: when unzipped the JavaScript tree complete history shows up in web browsers in the first report, but not in subsequent reports. The history appears to be present when the complete history file is unzipped and opened in a text editor. This happens for both the default filtering method and the tokenmatch method.

@timaber55 The tokenmatch method is a more accurate, but much slower filtering method than the default method. I don't know much more than that.

---

### Post by roggan87 on 2010-12-19
> **tetralectic said:**
> I'm getting an odd problem. I have the option for the complete history to be sent in zipped form checked in my account on the website. When I install/uninstall&reinstall Net Responsibility 2.0 in Ubuntu 10.10 64 bit, the first report sent includes the complete history in a JavaScript tree form as it should. However all in subsequent reports this JavaScript tree does not show up in the attached complete report when opened in Firefox 3.6.13, Chromium 10.0.615.0, Epiphany 2.30.2, or when I virtualize Windows 7 in VirtualBox, in Internet Explorer 8. When I open the report in a text editor such as gedit my history is there in the report file, it just doesn't render when opened in a web browser. This seems to happen whether I'm using the default filtering method or the tokenmatch method. So to recap: when unzipped the JavaScript tree complete history shows up in web browsers in the first report, but not in subsequent reports. The history appears to be present when the complete history file is unzipped and opened in a text editor. This happens for both the default filtering method and the tokenmatch method.

@timaber55 The tokenmatch method is a more accurate, but much slower filtering method than the default method. I don't know much more than that.

Oh no. Just to clarify, is it only the history, or the whole tree that refuses to render? Have you tried to uninstall/reinstall more than once with the same result (first report successful, and the rest broken)? It would help to see the reports, so you can attach them to an email so I can have a look, if it's ok with you. Thanks for letting me know, hope we can fix this bug!

@timaber55 Sorry I was unclear. You're using the tokenmatch if you've checked the checkbox "Always perform tokenmatch" in the configuration, or if you execute the command "sudo net-responsibility-report --tokenmatch". Otherwise you're using the default filtering method.

---

### Post by tetralectic on 2010-12-19
> **roggan87 said:**
> Oh no. Just to clarify, is it only the history, or the whole tree that refuses to render? Have you tried to uninstall/reinstall more than once with the same result (first report successful, and the rest broken)? It would help to see the reports, so you can attach them to an email so I can have a look, if it's ok with you. Thanks for letting me know, hope we can fix this bug!

... Hi roggan87

I have uninstalled & reinstalled many times with the same result. The first time I send out the report everything is fine, the whole JavaScript tree is rendered and opens appropriately :p. With all subsequent reports the whole JavaScript tree is missing from the rendering. When I open the subsequent reports this is all I get:[IMG]http://farm5.static.flickr.com/4028/5081240922_3bd8437062.jpg[/IMG]

No JavaScript tree :(
I'll get back with you regarding copies of the report files.

---

### Post by mpnordland on 2010-12-20
@roggan87 We need to use a proxy for catching user names I think that squid would be good, as tinyproxy doesn't work well with my computer.

---

### Post by mpnordland on 2010-12-22
@roggan87 We will need to switch from using urlsnarf to using squid for logging urls, and make squid require authentication. The authentication would be provided by the browser(or some other way) and would consist of the Net Responsibility username and password

---

### Post by roggan87 on 2010-12-23
> **mpnordland said:**
> @roggan87 We will need to switch from using urlsnarf to using squid for logging urls, and make squid require authentication. The authentication would be provided by the browser(or some other way) and would consist of the Net Responsibility username and password

Sounds interesting :) Unfortunately I'm having problems with my harddisk, which forces me to use windows for a while, until I've worked this out. However I agree urlsnarf is kind of limited to work with, squid does look promising. One strength with urlsnarf though is that it catches all internet traffic, not only the browsers. Maybe squid can do that as well?

If you have time, then please look at the usage of squid. I'll help you integrate it to Net Responsibility, when we know how to use it more precisely.

Merry Christmas :)

---

### Post by mpnordland on 2010-12-23
@roggan87 It would log all connections through a transparent proxy, all web connecting programs go through squid. We'll need to create an auth page that squid will at first redirect to, because transparent mode and authentication don't work together. The auth page should probably give the browser a cookie so that it doesn't have to keep re-authenticating.

---

### Post by mpnordland on 2010-12-27
actually, I found out that we don't need to give out a cookie, squid will automatically show the auth page again if there are no request's for a while, that 'a while' being specified by a timeout.

---

### Post by mrgronk on 2010-12-30
Hi,

Yesterday, I was doing an auto-refresh on my modem's status page, at one-second intervals, as my modem has been giving me grief with the occasional dropout.

The next net-responsibility report started at roughly 9:00 this morning, since my computer wasn't still running at midnight. Seven hours later, it's still running; it's been chewing up a full CPU equivalent throughout that time. I daren't stop it, because if I do, my understanding is that next time it'll just do the same again, only taking longer.

Since, apart from the status page, I wasn't doing any unconventional browsing, I can only suppose that's the problem - normally reports at the end of a day's browsing are done with after thirty minutes to an hour. (Nevertheless, I would argue that even 30 to 60 minutes is a long time.)

Maybe net-responsibility does this already, but if not, I think it might be a good idea to pre-process the URL log it keeps, removing duplicate entries. That might speed things up a bit before it starts the (presumably more expensive) pattern matching, and could be achieved via a system call to "sort -u" if a suitably quick sort doesn't already exist in Ruby. Thoughts?

---

### Post by mpnordland on 2010-12-30
sorry you had a problem, yes, I think ruby does have such a function, I'll try to find where it might be useful. 
Are you using tokenmatch? if you disable it you will get a less accurate report, but it may cut down on your cpu usage.
By the way, what modem do you have?

---

### Post by mrgronk on 2010-12-30
Well, the box in the web interface to "always use TokenMatch" is unchecked. Maybe that means TokenMatch is sometimes used, though.

My modem is a Motorola Surfboard SBG901.

---

### Post by mpnordland on 2010-12-31
ok, just wondering if maybe you and I had the same modem, ours gave me some headache a while ago. Anyway, if token match is off, then maybe you should try to clear the log some how, I don't know, I'll email roggan87 and see what he say's

---

### Post by mrgronk on 2011-01-01
Thanks, MP.

The log cleared yesterday (well, the day before, now), about 30 minutes after I first posted. So all's well there. For the most recent log, it took about 40 minutes to run.

I've had a look at the log - well, the one in /var/log anyway - and that seems to be mostly binary gibberish.

Hypothesis: the slow progress is a combination of Ruby, laborious pattern matching, and a six- or seven-year-old computer.

---

### Post by mrgronk on 2011-01-01
Also, how do I go about changing my accountability partner's email address on your website? I've tried editing the field, but when I click "Save and log out," the link just does nothing, click on it as I please. It's frustrating because the email address that reports have been going to is closing down (or already closed down) as of today.

I have been running NoScript, but I had explicitly allowed netresponsibility.com, and even disabling NoScript didn't help.

---

### Post by mpnordland on 2011-01-01
I'm not really involved in the website, but I think roggan87 will see your post and give you some help on that. One thing you could try would be just leave the original entry and add the new email address on a new line.

---

### Post by mpnordland on 2011-01-01
@roggan87 I think I've found what we are looking for: [NuFW]("http://www.nufw.org/projects/nufw/wiki/")

---

### Post by mrgronk on 2011-01-02
That didn't work, but thanks anyway. I'll keep any eye out for any words of advice from roggan87.

---

### Post by roggan87 on 2011-01-02
Sorry people, I haven't had time to answer questions.

@mrgronk: I'm not sure how you could speed up the reporting time. The first thing I'll start to work with after the stable release is to move the whole filtering process to the logger, which means that the URLs will be scanned instantly. The result is much faster reports. Until then, my only advice to speed up is to use less blacklists. That may of course be a risk, but better than not being able to use the software. The software should be pretty useful even if you only use the blacklist called "porn".

Regarding the website, I've seen that it's not working as expected, and I'll take care of that as soon as I get time. I hope I'll get time this coming week. Neither registration or configuration are working properly.

@mpnordland: Haven't had time to check out the softwares you've recommended, but it's of course interesting!

God bless!
Roggan

---

### Post by mrgronk on 2011-01-02
Thanks Roggan. I appreciate your work!

For myself, the two main flies in the ointment at the moment are (a) the time taken to process the reports, and (b) the appearance of large numbers of false positives. I like the idea of getting a stable release out there before working on these. Once the stable release has been done, would you like some help to address either or both?

---

### Post by sadastronaut on 2011-01-04
> **roggan87 said:**
> I shouldn't be too hard. Most of us are running Ubuntu or any other distro that's using the debian package system. That's why there's currently no rpm package for the latest releases. If you want, you can try to create an rpm file from the source. That requires EPM ([www.epmhome.org]("http://www.epmhome.org")). After you've installed EPM, download and unpack the source code, and run the following commands:
```
cd /the_source_code_folder/
sudo ./configure-packages
sudo ./make_rpm.sh
```If everything works out fine, you should have a new folder containing your fresh rpm.

If it's working, please let us know, so we can upload the rpm to the website.
Thanks!

I didn't have much luck with epm, although with alien I could successfully convert the deb package to an rpm, but I get ruby errors when I try to run.  I think it is just a little more difficult to get all the dependencies for the OpenSuSE platform.  If you happen to get the 2.0 version released as an rpm, I will try that.  

Also, if I need, I can always go to Ubuntu or Linux Mint to run the software.  Currently I'm using a Windows Proxy Server with Covenant Eyes.  

Thanks to all those doing work on this.

---

### Post by mpnordland on 2011-01-04
sorry, I was supposed to be working on that, but I was doing other things, I'll get to work on it immediately.

---

### Post by mpnordland on 2011-01-04
> **mpnordland said:**
> sorry, I was supposed to be working on that, but I was doing other things, I'll get to work on it immediately.
And things are moving forward now, I used susestudio to create and download a very minimalistic opensuse, and now I am working on compiling epm, and also having to download all the build tools and dependencies. I'll upload my working rpm once it exists :D

---

### Post by mpnordland on 2011-01-06
@roggan87
nufw didn't pan out, it is designed for over the network authorization, but check out this website, and tell me what you think: [http://www.linuxexpert.ro/Linux-Tutorials/squid-proxy-ncsa-authentication.html]("http://www.linuxexpert.ro/Linux-Tutorials/squid-proxy-ncsa-authentication.html")
edit:
ok, that works, but now, We have to figure out a way to keep users from changing stuff, right now, any browser savvy user would get around it in a second. Right now, if this were on a server, we could forge ahead into integrating it, but right now, we're stuck on how to force users to go through squid.

---

### Post by roggan87 on 2011-01-11
Net Responsibility 2.0 is now released as stable on the website. 
This time you'll have to uninstall the existing version before installing. Please get back with bug reports or any other problems you might run into.

@mpnordland: Sorry I haven't had time to check out and dive into your suggestions. All focus have been on the stable release. The next thing I'll work on is instant filtering, since Net Responsibility requires too much cpu power as it is now. I understand the importance of multiple users, but right now that's too much work. I really appreciate your work though, and I really hope we'll be able to implement it in a near future! BTW how is it going with the rpm?

All the best!

---

### Post by mpnordland on 2011-01-11
Don't worry, forcing users to go through it is not yet done yet anyway, The squid functionality is done, but I still have to get the one key thing working, which I'll not mention here, because it is the one thing that could easily disable everything.

---

### Post by tetralectic on 2011-01-14
> **roggan87 said:**
> Net Responsibility 2.0 is now released as stable on the website. 
This time you'll have to uninstall the existing version before installing. Please get back with bug reports or any other problems you might run into.

...

All the best!
It's very good to see. Congratulations to all who made this happen :D

---

### Post by tetralectic on 2011-01-14
> **roggan87 said:**
> Net Responsibility 2.0 is now released as stable on the website. 
This time you'll have to uninstall the existing version before installing. Please get back with bug reports or any other problems you might run into.

...

All the best!
It's very good to see. Congratulations to all who made this happen :D

---

### Post by mpnordland on 2011-01-18
[ATTACH]181455[/ATTACH]Can some one help me figuring this out? In trying to build the rpm I get this error, can someone tell me what package to install?

---

### Post by roggan87 on 2011-01-19
> **mpnordland said:**
> [ATTACH]181455[/ATTACH]Can some one help me figuring this out? In trying to build the rpm I get this error, can someone tell me what package to install?

Are you running as root? If not, try doing so.

[http://forums.opensuse.org/archives/sf-archives/archives-network-internet/324821-where-ifconfig-iwconfig.html](http://forums.opensuse.org/archives/sf-archives/archives-network-internet/324821-where-ifconfig-iwconfig.html)

Thanks for working with the rpm, it will really be useful!

---

### Post by mpnordland on 2011-01-19
That might be it, but as this is a customized distro of opensuse, it just might not be there. anyway I give it try :D

---

### Post by mpnordland on 2011-01-19
That was it, thanks!
However, packaging failed with epm, so I not sure what now. I go back through the dependencies and see if I missed something

---

### Post by mpnordland on 2011-01-19
Ok, I have all the dependencies installed, it still didn't work, so I found an rpm for it, and I'm working on it and it's dependencies. I get back to you guy's when that's done as to whether it worked or not
EDIT
well, still no go. I'll appeal to your higher wisdom roggan87, what do you think?

---

### Post by roggan87 on 2011-01-19
> **mpnordland said:**
> Ok, I have all the dependencies installed, it still didn't work, so I found an rpm for it, and I'm working on it and it's dependencies. I get back to you guy's when that's done as to whether it worked or not
EDIT
well, still no go. I'll appeal to your higher wisdom roggan87, what do you think?

Don't know about that higher wisdom :) When it comes to packaging I'm no expert. I'd really like to see the output though. I might be able to help in some way. So please post you output, that's what I think :P

---

### Post by sadastronaut on 2011-01-19
> **mpnordland said:**
> Ok, I have all the dependencies installed, it still didn't work, so I found an rpm for it, and I'm working on it and it's dependencies. I get back to you guy's when that's done as to whether it worked or not
EDIT
well, still no go. I'll appeal to your higher wisdom roggan87, what do you think?

Is it a build error, or does it occur when you are trying to run it?

---

### Post by mpnordland on 2011-01-19
It's a build error. I'm (as you might have noticed) doing this thing in a very minimal version of opensuse under virtual box, so a screen shot of the output will have to work[ATTACH]181504[/ATTACH]

---

### Post by sadastronaut on 2011-01-19
> **mpnordland said:**
> It's a build error. I'm (as you might have noticed) doing this thing in a very minimal version of opensuse under virtual box, so a screen shot of the output will have to work[ATTACH]181504[/ATTACH]

yeah, i got a similar issue when i tried.

---

### Post by roggan87 on 2011-01-20
> **mpnordland said:**
> It's a build error. I'm (as you might have noticed) doing this thing in a very minimal version of opensuse under virtual box, so a screen shot of the output will have to work[ATTACH]181504[/ATTACH]

Yeah, that's about as far as I get when I try to compile an rpm-package under Ubuntu.

Instead of running ./make_rpm.sh you can run the following command (which almost does the same thing, but tells us a little more info)
```
epm -v -n -f rpm netresponsibility -v
```

When I run that command my machine is complaining about missing files. Please try that command, and post the output here :)

---

### Post by roggan87 on 2011-01-20
After some copy-paste I managed to create some rpm-packages. See attachment. Both for 32-bit and 64-bit. I changed the dependencies in the alternative versions according to this post:
[https://bugs.launchpad.net/netresponsibility/+bug/693626/comments/2](https://bugs.launchpad.net/netresponsibility/+bug/693626/comments/2)

I'd be glad if you guys tried the packages and came with feedback whether there working or not. And of course which package that's working best.

Good luck :)

---

### Post by mpnordland on 2011-01-20
yep, the same here, I'm not sure what is the prob, maybe the list file is setup wrong

---

### Post by roggan87 on 2011-01-21
> **mpnordland said:**
> yep, the same here, I'm not sure what is the prob, maybe the list file is setup wrong

Did you try the rpm-packages I attached?

---

### Post by mpnordland on 2011-01-21
not yet, but I will!
Later:
I tried it, in opensuse the package name are different than in ubuntu. I have all the equivalent packages installed, but the rpm doesn't work because it doesn't have the packages with those exact names. I be looking at and fixing this.

---

### Post by mpnordland on 2011-01-21
Well, instead of doing that, I actually did some more work on the gui, kinda. The python YAML implementation works weird for dumping(writing) the file, it removes all the comments, and just writes the dictionary to the file. This just won't do, so I've started on a config-parser module, right now the read_config() function is done, and I'm working on write_config, and when it's done, it will leave the .conf looking like it did when it started with it. TTFN!

---

### Post by mpnordland on 2011-01-22
double post

---

### Post by mpnordland on 2011-01-22
I propose a branching of this project. The current setup works really well for single user computers. The multiuser accountability system I'm working on will work well for multiusers, but what I'm concerned about is that the multiuser setup may have some overhead that's not necessary for just a single user. Most of us know the acronym: KISS or Keep It Simple. Hence the proposed branch: Net Responsibility single-user and Net Responsibility multi-user, and maybe, even Net Responsibility server. If server would come about, it would be a rather simple mod of multi-user, and single-user would be the same current setup as now. I don't like to install anything on my system that is not absolutely necessary (I make some exceptions for games :) ). That concern needs to extend to how much we require that the user install for Net Responsibility to work. For just one user, the setup for the multi-user is overkill, and may lead to performance problems that aren't worth the usefulness (yes I know, getting rid of addictions is VERY important, but if Net Responsibility makes the internet practically unusable...) on the other hand, single-user, is just not enough features for multiple users. I think that a branch will enable us to provide usability that is suited to both types of use. Long Post! That all for now.

---

### Post by mpnordland on 2011-01-25
ok, the write_config() function is complete, except for the fact that it doesn't work. It should do all that I want it to do, except somewhere, I have something wrong, and it never writes anything to the file, I think it has something to do with the mode I use for opening the file, so I'll check on that, on the issue of the rpm, I have yet to get things to cooperate all at the same time, so I haven't done any thing on that, and on top of all this, I'm supposed to also be setting up a web content filter for my network... I'm sorta swamped at the moment! The config-parse module is attached, for those who might be able to fix it.

---

### Post by mpnordland on 2011-01-25
some dumb mistake was posted here, but I removed it :)

---

### Post by roggan87 on 2011-01-27
Micah, you're really involved in every bit of this project :)

Did you try the alternative package as well? In that one I changed the dependencies to fit openSUSE.

I like the idea of multiuser as a branch! I've been thinking about the same, so let's strive towards that.

Regarding the config, Net Responsibility is refreshing the file on a regular basis, so it doesn't matter if you write any data to it, since it'll be overwritten. Therefor you have to submit the changes to the webserver, so the settings can be changed there. You should rather look at how to submit data to the server.

You need to send the variables "online_user" and "online_password" to the server. As a start you can send those values to [http://www.http://netresponsibility.com/request/config.php](http://www.http://netresponsibility.com/request/config.php) and see what response you get. If the data is correct, you'll get the whole config file, otherwise you'll get an error message.

So start in that end, and when it's working as supposed, I'll help you to also store the data in the database. (By creating another page that actually does that.)

Good luck

---

### Post by mpnordland on 2011-01-27
well, The intent of the config parser was so that I could do some moding on the config file without destroying all the comments! I wasn't intending to turn it into anything else. I'll try the alternative, as when I unpacked it, I didn't know what it was there for!

---

### Post by mpnordland on 2011-02-08
Well, after a very busy week working on a presentation, I've done none of the stuff I was going to do, but I have looked into squid log file analyzers, one or two at least look like we could use them, however, the one I am leaning toward outputs in html, although it does look like it also can output in a format suitable for emailing, so, if maybe one of the web wizards,(we have a rather nice website, so one or two of them must be around here somewhere :) ) can think of a way to extract what we want from html, then I'll look more into it.

---

### Post by roggan87 on 2011-02-09
> **mpnordland said:**
> Well, after a very busy week working on a presentation, I've done none of the stuff I was going to do, but I have looked into squid log file analyzers, one or two at least look like we could use them, however, the one I am leaning toward outputs in html, although it does look like it also can output in a format suitable for emailing, so, if maybe one of the web wizards,(we have a rather nice website, so one or two of them must be around here somewhere :) ) can think of a way to extract what we want from html, then I'll look more into it.

Sounds really interesting! Extracting information from html shouldn't be too hard :) If you email one or more examples, then I can look at it and see how to use it. Does the log analyzers filter or sort the information as well, or is that a job to do after extracting?

There's no panic on getting the other things done. Of course we're excited about it, but take the time you need. I really appreciate the work you're putting into this project!

By the way, I'm working on a new alpha that's soon ready for release. It'll contain some interesting features but I'll get back with details. I've done some modifications in send_report.py, and if you want to you could just double-check if there a better way to do it. I'd also like if you wanted to add a feature, very small but still.

But as I said, don't panic, take your time.
Blessings!

---

### Post by mpnordland on 2011-02-09
well, according to their sparse website, it can report right down to where they went, and that is just what we want, I am looking into how all it is presented. I forget if it can do realtime or not, so I'll have to look into it.

---

### Post by roggan87 on 2011-02-11
New release!
I've uploaded a new alpha version to the [website]("http://www.netresponsibility.com/download.php"). It's called 2.0.1 and these are the most important updates:
[LIST]
[*]**Instant filtering.** Instead of scanning all URLs at report time, they're scanned quickly in realtime. Only flagged URLs gets filtered at report time, this time with a more advanced method.
[*]**Instant reports.** The accountability partner gets an email instantly when inappropriate content is being watched. You have to set the sensitivity on the website with the option called "instant threshold".
[*]**Some other minor changes.**
[/LIST]

Please try out this version and come with feedback. Let me know if the instant filtering is working or if it's getting too heavy for your system. I'm also interested in how the instant reports are working, and what threshold's working good.

Good luck with this one!

---

### Post by mpnordland on 2011-02-11
whoaaa, I just see the headlines:
Net Responsibility joins Google in pioneering Instant results! :)
really great roggan87 that is really cool.

---

### Post by duncanbell1 on 2011-02-13
Hi folks,

I'm having a few issues getting this working. I've had (2.0) working before, but I reformatted my machine and have started with a fresh install of Ubuntu 10.10 this morning. I've downloaded and installed Net Responsibility 2.0 from the DEB file. 

Trying to perform a test mail produces this:
Downloading the configurationfile...
Saving it.
/usr/share/net-responsibility/lib/server_connection.rb:50:in `-': nil can't be coerced into Bignum (TypeError)
    from /usr/share/net-responsibility/lib/server_connection.rb:50:in `get_blacklists'
    from /usr/share/net-responsibility/lib/options.rb:217:in `update_settings'
    from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
    from /usr/local/bin/net-responsibility-report:94:in `new'
    from /usr/local/bin/net-responsibility-report:94:in `initialize'
    from /usr/local/bin/net-responsibility-report:151:in `new'
    from /usr/local/bin/net-responsibility-report:151

and if I tell it to report from the Config GUI I get the same. I've checked Ruby's installed and is the latest version from the reps. Is there some other dependency I'm missing? 

I've deleted my Net Responsibility account and then recreated it in case it was a problem from the web end, but to no avail.
Any help would be greatly appreciated - I've found Net Responsibility so very helpful in the past, and am really keen to get it working again!

Many thanks!

Duncan

---

### Post by roggan87 on 2011-02-14
> **duncanbell1 said:**
> Hi folks,

I'm having a few issues getting this working. I've had (2.0) working before, but I reformatted my machine and have started with a fresh install of Ubuntu 10.10 this morning. I've downloaded and installed Net Responsibility 2.0 from the DEB file. 

Trying to perform a test mail produces this:
Downloading the configurationfile...
Saving it.
/usr/share/net-responsibility/lib/server_connection.rb:50:in `-': nil can't be coerced into Bignum (TypeError)
    from /usr/share/net-responsibility/lib/server_connection.rb:50:in `get_blacklists'
    from /usr/share/net-responsibility/lib/options.rb:217:in `update_settings'
    from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
    from /usr/local/bin/net-responsibility-report:94:in `new'
    from /usr/local/bin/net-responsibility-report:94:in `initialize'
    from /usr/local/bin/net-responsibility-report:151:in `new'
    from /usr/local/bin/net-responsibility-report:151

and if I tell it to report from the Config GUI I get the same. I've checked Ruby's installed and is the latest version from the reps. Is there some other dependency I'm missing? 

I've deleted my Net Responsibility account and then recreated it in case it was a problem from the web end, but to no avail.
Any help would be greatly appreciated - I've found Net Responsibility so very helpful in the past, and am really keen to get it working again!

Many thanks!

Duncan

Hi Duncan, we're glad you like the software and we'll try to help you!
I think there might be something in the settings that's causing this bug. If you let me know your username I can check them out. You can PM me in that case.

Robert

---

### Post by duncanbell1 on 2011-02-14
Thanks Robert,

I've just PM'ed you this, but after you saying it was the settings I went a-hunting, and it appears that toggling the "tokenmatch" button seems to have fixed the issue, so I presume it was a bug with something there, but the program will now happily send reports out. Thanks for your help guys!

Duncan

---

### Post by tetralectic on 2011-02-15
I'm having some trouble installing and configuring the new 64-bit Net Responsibility 2.0.1 alpha :(. When running dpkg -i on the deb file I get an install error
```
sudo dpkg -i netresponsibility-2.0.1.amd64.deb
Selecting previously deselected package netresponsibility.
(Reading database ... 476082 files and directories currently installed.)
Unpacking netresponsibility (from netresponsibility-2.0.1.amd64.deb) ...
Setting up netresponsibility (2.0.1) ...
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
update-rc.d: warning: net-responsibility-daemon start runlevel arguments (2) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: net-responsibility-daemon stop runlevel arguments (0) do not match LSB Default-Stop values (0 1 6)
 * Starting the Net Responsibility daemon net-responsibility-daemon             /etc/init.d/net-responsibility-daemon: Starting net-responsibility-daemon
Downloading the configurationfile...
/usr/share/net-responsibility/lib/syslog.rb:33:in `log': Process name not set (SyslogError)
    from /usr/share/net-responsibility/lib/syslog.rb:58:in `log_exception'
    from /usr/share/net-responsibility/lib/syslog.rb:58:in `each'
    from /usr/share/net-responsibility/lib/syslog.rb:58:in `log_exception'
    from /usr/local/bin/net-responsibility-daemon:146:in `initialize'
    from /usr/local/bin/net-responsibility-daemon:157:in `new'
    from /usr/local/bin/net-responsibility-daemon:157
                                                                         [[COLOR=Red]fail[/COLOR]]
dpkg: error processing netresponsibility (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 netresponsibility

```I configure it with my user name and password and then send a test mail. The test mail never arrives. This is the output of running the test mail:
```
/usr/share/net-responsibility/lib/server_connection.rb:86:in `initialize': No such file or directory - /usr/share/net-responsibility/lib/lists.lst (Errno::ENOENT)
    from /usr/share/net-responsibility/lib/server_connection.rb:86:in `open'
    from /usr/share/net-responsibility/lib/server_connection.rb:86:in `modified_file'
    from /usr/share/net-responsibility/lib/server_connection.rb:38:in `update_config_blacklist'
    from /usr/share/net-responsibility/lib/options.rb:225:in `update_settings'
    from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
    from /usr/local/bin/net-responsibility-report:94:in `new'
    from /usr/local/bin/net-responsibility-report:94:in `initialize'
    from /usr/local/bin/net-responsibility-report:150:in `new'
    from /usr/local/bin/net-responsibility-report:150
```There appears to be a run time error. I also cannot find a daemon process running as root under ruby as one would for the stable Net Responsibility 2.0.

Any help sorting this out would be much appreciated.

---

### Post by roggan87 on 2011-02-16
> **tetralectic said:**
> I'm having some trouble installing and configuring the new 64-bit Net Responsibility 2.0.1 alpha :(. When running dpkg -i on the deb file I get an install error
```
sudo dpkg -i netresponsibility-2.0.1.amd64.deb
Selecting previously deselected package netresponsibility.
(Reading database ... 476082 files and directories currently installed.)
Unpacking netresponsibility (from netresponsibility-2.0.1.amd64.deb) ...
Setting up netresponsibility (2.0.1) ...
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
update-rc.d: warning: net-responsibility-daemon start runlevel arguments (2) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: net-responsibility-daemon stop runlevel arguments (0) do not match LSB Default-Stop values (0 1 6)
 * Starting the Net Responsibility daemon net-responsibility-daemon             /etc/init.d/net-responsibility-daemon: Starting net-responsibility-daemon
Downloading the configurationfile...
/usr/share/net-responsibility/lib/syslog.rb:33:in `log': Process name not set (SyslogError)
    from /usr/share/net-responsibility/lib/syslog.rb:58:in `log_exception'
    from /usr/share/net-responsibility/lib/syslog.rb:58:in `each'
    from /usr/share/net-responsibility/lib/syslog.rb:58:in `log_exception'
    from /usr/local/bin/net-responsibility-daemon:146:in `initialize'
    from /usr/local/bin/net-responsibility-daemon:157:in `new'
    from /usr/local/bin/net-responsibility-daemon:157
                                                                         [[COLOR=Red]fail[/COLOR]]
dpkg: error processing netresponsibility (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 netresponsibility

```I configure it with my user name and password and then send a test mail. The test mail never arrives. This is the output of running the test mail:
```
/usr/share/net-responsibility/lib/server_connection.rb:86:in `initialize': No such file or directory - /usr/share/net-responsibility/lib/lists.lst (Errno::ENOENT)
    from /usr/share/net-responsibility/lib/server_connection.rb:86:in `open'
    from /usr/share/net-responsibility/lib/server_connection.rb:86:in `modified_file'
    from /usr/share/net-responsibility/lib/server_connection.rb:38:in `update_config_blacklist'
    from /usr/share/net-responsibility/lib/options.rb:225:in `update_settings'
    from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
    from /usr/local/bin/net-responsibility-report:94:in `new'
    from /usr/local/bin/net-responsibility-report:94:in `initialize'
    from /usr/local/bin/net-responsibility-report:150:in `new'
    from /usr/local/bin/net-responsibility-report:150
```There appears to be a run time error. I also cannot find a daemon process running as root under ruby as one would for the stable Net Responsibility 2.0.

Any help sorting this out would be much appreciated.

Hi!

I've uploaded a new version of Net Responsibility 2.0.1. Please try if that one is working better for you. Thanks for feedback :)

---

### Post by tetralectic on 2011-02-16
> **roggan87 said:**
> Hi!

I've uploaded a new version of Net Responsibility 2.0.1. Please try if that one is working better for you. Thanks for feedback :)
Hi roggan87

Thanks for the new version of Net Responsibility 2.0.1 :p. I am however, still getting an install error on my 64-bit machine :(:
```
sudo dpkg -i netresponsibility-2.0.1.amd64.deb
Selecting previously deselected package netresponsibility.
(Reading database ... 476082 files and directories currently installed.)
Unpacking netresponsibility (from netresponsibility-2.0.1.amd64.deb) ...
Setting up netresponsibility (2.0.1) ...
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
update-rc.d: warning: net-responsibility-daemon start runlevel arguments (2) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: net-responsibility-daemon stop runlevel arguments (0) do not match LSB Default-Stop values (0 1 6)
 * Starting the Net Responsibility daemon net-responsibility-daemon             /etc/init.d/net-responsibility-daemon: Starting net-responsibility-daemon
Downloading the configurationfile...
/usr/share/net-responsibility/lib/syslog.rb:33:in `log': Process name not set (SyslogError)
    from /usr/share/net-responsibility/lib/syslog.rb:58:in `log_exception'
    from /usr/share/net-responsibility/lib/syslog.rb:58:in `each'
    from /usr/share/net-responsibility/lib/syslog.rb:58:in `log_exception'
    from /usr/local/bin/net-responsibility-daemon:144:in `initialize'
    from /usr/local/bin/net-responsibility-daemon:155:in `new'
    from /usr/local/bin/net-responsibility-daemon:155
                                                                         [[COLOR=Red]fail[/COLOR]]
dpkg: error processing netresponsibility (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 netresponsibility
```

---

### Post by roggan87 on 2011-02-18
Sorry to hear that tetralectic.
One quick question; do you have Internet access during the installation?

---

### Post by mpnordland on 2011-02-18
Hmm, I ought to give that a try, although, I'm running a 32-bit computer. roggan87: Eureka! I've found a command to block internet access. I now have just to get some more stuff done on the proxy, and then we can move on to parsing logs

---

### Post by tetralectic on 2011-02-18
> **roggan87 said:**
> Sorry to hear that tetralectic.
One quick question; do you have Internet access during the installation?
Hi roggan87

Yes do do have Internet access during the installation. I was thinking that my recent problems with my Net Responsibility account was causing the install problems with 64-bit 2.0.1, but that seems to have been fixed and 64-bit Net Responsibility 2.0 is working just fine :D.

From my reading of the dpkg -i output it looks as though it's trying to download the configuration files during the install, but I haven't configured it yet with my account name and password to be able to access my Net Responsibility account :confused:. Could this be the problem?

After the install of 2.0.1  daemon does not run. It also does not run after a reboot of my computer :-(. I'll have a closer look to see if the daemon briefly starts during the install process before falling over.

---

### Post by mpnordland on 2011-02-18
try configuring net-responsibility then restarting your computer.

---

### Post by roggan87 on 2011-02-19
> After the install of 2.0.1 daemon does not run. It also does not run after a reboot of my computer

Hmm...

What happens when you run these commands respectively:
```
sudo net-responsibility-daemon --version
```
```
sudo net-responsibility-daemon --nodaemon
```

Can you configure as expected? Look in /etc/net-responsibility.conf to see if your username is stored there.

> From my reading of the dpkg -i output it looks as though it's trying to download the configuration files during the install, but I haven't configured it yet with my account name and password to be able to access my Net Responsibility account . Could this be the problem?
It could be the problem. Weird though that this bug haven't appeared before in earlier versions...

---

### Post by tetralectic on 2011-02-19
> **mpnordland said:**
> try configuring net-responsibility then restarting your computer.
Hi mpnordland

Thanks for the suggestion but I had already tried that :)

---

### Post by roggan87 on 2011-02-21
> **tetralectic said:**
> Hi mpnordland

Thanks for the suggestion but I had already tried that :)

Still curious on your output of *"sudo net-responsibility-daemon --nodaemon"* though ;)

---

### Post by garrettendi on 2011-02-27
Hello,

Firstly, thanks for creating such a fantastic application. It is refreshing to know that there are developers who are aware that there are other Christians who use Linux.... According to companies like Covenant Eyes, Linux is some kind of dark land....

Anyhoo, my question: I'm a security nut and want to configure Firestarter so it doesn't prevent Net Responsibility from doing it's job. What are the steps I need to take? I'm not new to Linux, but I've always been a bit of a slow learner when it comes to configuring firewalls.

Cheers!

---

### Post by mpnordland on 2011-02-27
actually, It is quite easy. Just don't block port 80 and you'll be fine!
Net-responsibility just uses urlsnarf from dsniff to track everything

---

### Post by roggan87 on 2011-03-04
Ok, just thought I'd let you get some insight into the lab.
Currently I'm working on reducing the number of false positives, and it's going very well. Right now only 10-20% of the false positives makes it through the tests. Your improvement data have been extremely useful here.
I've also been thinking a little of the layout and graphical profile. I've wondered back and forth what could be a good symbol for Net Responsibility, and it's a little hard. Finally I think I've decided it will be a soap bar. What? That's right, a soap bar. But why? Because "purity requires honesty". Net Responsibility is all about staying clean, by being honest. If you think it's a worthless idea, then please let me know. I've uploaded a preview of some changes for the website [here]("http://netresponsibility.com/new/"). The plan is to replace the old green logo with [this soap bar]("http://netresponsibility.com/new/img/logo_256.png") (or something similar to it). The phrase "purity requires honesty" will be kind of a slogan for Net Responsibility. Other ideas are welcome here!

Some feautures I'd like to see in the future (I'm not saying near future though) is:
[LIST]
[*]time-blocking (Net Responsibility will report all websites visited during forbidden time periods. These periods will be set by the user, could be 10.00pm-5.30am for example.)
[*]Graded warnings (like low, medium or high strength). I think that might help the accountability partner.
[*]Multiuser support, different accounts on the same computer. Micah is working on this part, which will be a branch of this project.
[*]SMS reports. Not sure this is possible though. It would be perfect for the instant reports.
[/LIST]

I think that's all for now, if you haven't tried the latest alpha 2.0.1 yet, then consider doing that. It's more accurate and runs smoother.
Be blessed, and thank you all who are involved in this project in any way!

---

### Post by sadastronaut on 2011-03-04
I think the bar of soap is a great logo.  The "NR" is a little hard to read however, so if you did something with shading, it would make the letters pop out a little more.  

> **roggan87 said:**
> Ok, just thought I'd let you get some insight into the lab.
Currently I'm working on reducing the number of false positives, and it's going very well. Right now only 10-20% of the false positives makes it through the tests. Your improvement data have been extremely useful here.
I've also been thinking a little of the layout and graphical profile. I've wondered back and forth what could be a good symbol for Net Responsibility, and it's a little hard. Finally I think I've decided it will be a soap bar. What? That's right, a soap bar. But why? Because "purity requires honesty". Net Responsibility is all about staying clean, by being honest. If you think it's a worthless idea, then please let me know. I've uploaded a preview of some changes for the website [here]("http://netresponsibility.com/new/"). The plan is to replace the old green logo with [this soap bar]("http://netresponsibility.com/new/img/logo_256.png") (or something similar to it). The phrase "purity requires honesty" will be kind of a slogan for Net Responsibility. Other ideas are welcome here!

Some feautures I'd like to see in the future (I'm not saying near future though) is:
[LIST]
[*]time-blocking (Net Responsibility will report all websites visited during forbidden time periods. These periods will be set by the user, could be 10.00pm-5.30am for example.)
[*]Graded warnings (like low, medium or high strength). I think that might help the accountability partner.
[*]Multiuser support, different accounts on the same computer. Micah is working on this part, which will be a branch of this project.
[*]SMS reports. Not sure this is possible though. It would be perfect for the instant reports.
[/LIST]

I think that's all for now, if you haven't tried the latest alpha 2.0.1 yet, then consider doing that. It's more accurate and runs smoother.
Be blessed, and thank you all who are involved in this project in any way!

---

### Post by mpnordland on 2011-03-04
Totally dig the new garb for the website. I started on a new logo a while ago, but I didn't have any good ideas.

---

### Post by mpnordland on 2011-03-04
Some news from the multi user branch: We will be using sarg to get the urls from the squid logs. sarg can output to stdout, and it's intended purpose is to show who is going where. Once I can jury rig it right so that it generates what we want, then I'll be ready to integrate it into the net-resposibilty reporting. 
@roggan87: We'll need to add checking if the squid process is live and indicate a shutdown in the report if it isn't. I'm not sure how to do that, so when I get there I'll be asking :)

---

### Post by mpnordland on 2011-03-05
And on the gui front I have the configure module (that will eventually power all of the cool abilities that the gui will have)has it's basics almost down. I have gotten the write_config method almost done, just a few more things clear up, and then I can get some of the stuff done on the gui that has been waiting for this.

---

### Post by mpnordland on 2011-03-05
and for those who want bleeding edge up-to-date here is a preview of some of the things in store for you. the blacklist/whitelist tab is not functional. I have fianlly gotten rid of the extra "configuration finished"! there is a demo .conf file supplied. I **DON'T** advise trying to use this on your real config file, while everything should remain functional, it could foul things up.

---

### Post by mpnordland on 2011-03-05
Ever have a problem that you can't figure out? And then after a while come up with a really simple idea to fix it? I just had that happen. I'm happy to announce that the work on the gui can now move forward some, because the configure module is initially complete, on the other hand, I will have to keep working on it because I just took a look at the new .conf, I see lots of possibilities!
updated configure module below, if you downloaded the new gui preview above, just drag this into the "gui" folder in the folder where you extracted it.

---

### Post by roggan87 on 2011-03-10
Micah, it looks promising :)

I've uploaded a new alpha (2.0.2) today. The most important update compared to 2.0.1 is better accuracy to avoid false positives.

Feel free to check it out!

---

### Post by mpnordland on 2011-03-10
@roggan87 can you explain this section of the config file?
```
whitelist:
  Whitelist:
    - ^(www.)?netresponsibility.com
```
it seems a little redundant, and it messes with my neat little scheme for parsing it :)

---

### Post by roggan87 on 2011-03-12
> **mpnordland said:**
> @roggan87 can you explain this section of the config file?
```
whitelist:
  Whitelist:
    - ^(www.)?netresponsibility.com
```
it seems a little redundant, and it messes with my neat little scheme for parsing it :)

I know, it's not good-looking, I guess it depends on me being lazy. Let's just say that it's a shortcut in the programming, but I know it should have been done better.

If you want, I can change it for the next alpha, 2.0.3. Of course it should look like this:
```
whitelist:
  - ^(www.)?netresponsibility.com
```

---

### Post by mpnordland on 2011-03-12
That probably would be best, how is it a shortcut? this sounds interesting.

---

### Post by mpnordland on 2011-03-12
I've just finished adding functionality to the gui that changes the process name, and also add's the new Icon to the window and the window list.

---

### Post by mpnordland on 2011-03-14
I've started initial sarg configuration on the multiuser branch.

---

### Post by mpnordland on 2011-03-15
I've finished putting together my stratagy for reading the config file, and I'll soon get it implemented in the configure module.

Half hour later: Just did it. It works thus:
everything goes into a dictionary as before,

```
var: something
```

adds 'var' to the dictionary, 'var' points to 'something'

```
var2: 
  -part1
  -part2

```
adds 'var2' to the dictionary, 'var2' points to a list containing ' -part1' and ' -part2'
that extra space in front is not intentional, but I haven't found a nice way to get rid of it yet.
This will work with the old config file too.
as far as I know, not having it there won't stop my module from parsing it, but it would probably mess with a "real" YAML parser.
I'll upload the new module when the write_config function is done.

---

### Post by mpnordland on 2011-03-16
Alright, I have the write_config function done. While I was working on it, I found and fixed a bug in the read_config function. Fixing the bug means that there must be that space in front of the dash that delimits a list.
```

var2: 
  -part1
  -part2
 ^

```
Now does it make sense? 
Just look at the read_config function if it doesn't.

---

### Post by martinquested on 2011-03-21
Hello.  I have been unable to delete an account on the website.  After entering the Captcha code correctly I just get a page declaring "Sorry, wrong security code" and the account is not deleted.

This is causing a problem since (without warning) my Net Responsibility seems to have stopped working in January, and the error I see when I run the config script or gui is:
```
Another account have already been set up on your computer, (marq2). Please delete that account before you use this one.   from /usr/local/bin/net-responsibility-config-cli:108:in `initialize'

```

It is true, I did apparently set up both marq and marq2 on this computer.  Only marq is needed, so I'd be very grateful to find out how to remove marq2.  I can't find anything pointing to it on the computer - though I admit I'm not completely sure where to look.

---

### Post by roggan87 on 2011-03-25
> **martinquested said:**
> Hello.  I have been unable to delete an account on the website.  After entering the Captcha code correctly I just get a page declaring "Sorry, wrong security code" and the account is not deleted.

This is causing a problem since (without warning) my Net Responsibility seems to have stopped working in January, and the error I see when I run the config script or gui is:
```
Another account have already been set up on your computer, (marq2). Please delete that account before you use this one.   from /usr/local/bin/net-responsibility-config-cli:108:in `initialize'

```

It is true, I did apparently set up both marq and marq2 on this computer.  Only marq is needed, so I'd be very grateful to find out how to remove marq2.  I can't find anything pointing to it on the computer - though I admit I'm not completely sure where to look.

I'm sorry for this, will look at it. I removed your account, marq2, manually. Thanks for pointing out.

Take care!

---

### Post by mpnordland on 2011-03-25
Just a quick note, when using the new website, the downloads don't work, as the files the links point to don't exist. Once this becomes the regular page, this issue should disappear.

---

### Post by martinquested on 2011-03-28
> **roggan87 said:**
> I'm sorry for this, will look at it. I removed your account, marq2, manually. Thanks for pointing out.

Take care!

Thanks, that worked.  Now the only problem is that the whitelist is being ignored.

---

### Post by mpnordland on 2011-03-28
Hi, I've created a Google Groups mailing list for help and support for Net Responsibility. You can sign up with your email address and post questions through the Google Groups web interface, or by emailing [email]net-responsibility-support@googlegroups.com[/email] with your problem. This list should just be for when your having problems. It will also keep separate discussions separate.
 I'm thinking about creating a group for development as well, so that help and support is neatly divided from dev discussions.

---

### Post by roggan87 on 2011-03-30
Micah, sorry I haven't replied to your posts.
Thanks for pointing out the downloads section, it will work as soon as it goes live.
The other posts sounds interesting. I'm following the progress. Thanks for your work.

---

### Post by mpnordland on 2011-04-01
Check this out, [Canterbury Distribution  ]("http://www.opensuse.org/") This ought to make things easier for packaging to say the least.
Another thing, we are the number one google result for "Net Responsibility"
Oh, and guess what, the Canterbury distro was an April fools joke. This is the first that I wish was real.

---

### Post by semijoyful on 2011-04-06
Not sure if this has been addressed yet, but I encountered an issue trying to install Net Responsibility on the beta version of ubuntu 11.04 64 bit:

Hello!  I first want to say that I am very thankful for this program; it has been effective in the same ways I have experienced quality programs like Covenant Eyes for Windows.  I am running the beta version of Ubuntu  11.04, and I am not able to install the 2.0 .deb for AMD64 package.  It says that the package is of bad quality, and it refuses to install.  I have attached a screenshot for your reference.  Any way I can force install this .deb package?  Any assistance with this would be greatly appreciated.  Thanks!

Sincerely,
Kirk

---

### Post by tetralectic on 2011-04-06
> **semijoyful said:**
> Not sure if this has been addressed yet, but I encountered an issue trying to install Net Responsibility on the beta version of ubuntu 11.04 64 bit:

Hello!  I first want to say that I am very thankful for this program; it has been effective in the same ways I have experienced quality programs like Covenant Eyes for Windows.  I am running the beta version of Ubuntu  11.04, and I am not able to install the 2.0 .deb for AMD64 package.  It says that the package is of bad quality, and it refuses to install.  I have attached a screenshot for your reference.  Any way I can force install this .deb package?  Any assistance with this would be greatly appreciated.  Thanks!

Sincerely,
Kirk
Hi semijoyful

This is a known issue with 11.04 beta, see

[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/712377](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/712377)

Try

```
$ sudo apt-get install gdebi

``` and then
```

 $ sudo gdebi name_of_deb_package_here.deb

```or instead

```
sudo dpkg -i name_of_deb_package_here.deb
```I haven't tried this, I'm still running 10.10, so I hope this works.

---

### Post by mpnordland on 2011-04-06
I tried installing natty, but I was not impressed by the quality of the beta, so I'm right now back to 10.10

---

### Post by mpnordland on 2011-04-09
So, where do we host our code? I've been wanting to get a development branch setup on my computer, and my only prob is that I don't know where the code is hosted.

---

### Post by roggan87 on 2011-04-11
> **mpnordland said:**
> So, where do we host our code? I've been wanting to get a development branch setup on my computer, and my only prob is that I don't know where the code is hosted.

Before I got involved, we hosted the code at [sourceforge]("http://sourceforge.net/projects/responsibility/"). Then I started to develop the software, and I've only been hosting the code on the [website]("http://www.netresponsibility.com"). Then Rohn created a [Launchpad page]("https://launchpad.net/netresponsibility") to be able to report bugs. Now the latest thing that happened is the Google Group. I feel like the project is very split up. I'm probably the main cause for this, since I don't have any experience in open source programming. But the question remains, where do we host the code?

Do you have any experience from launchpad or sourceforge? Which one is easier for branches etc?

I've also kind of started a branch. I'm rewriting parts of the project in c++. The goal is to write all code in c++, cause then it would be remarkably faster, less dependent on other software and hopefully easier to make it cross-platform compatible.

Take care!

---

### Post by mpnordland on 2011-04-11
I have some experience on source-forge, administering a project that I created, so I would tend to lean towards that. It also let's each project have it's own forum too. As to ease of use, I understand that launchpad could auto build our .deb packages, whereas source-forge can't (to my knowledge). But, source-forge will let you use whatever versioning system you want, e.g. SVN git, Launchpad uses just bazzar. I prefer svn because there is a great tool called RabbitVCS that I like to use for versioning and it supports SVN.
And, sorry about just going ahead on the google group, I probably should have discussed it here first.

---

### Post by Jordy_224 on 2011-04-12
Where can one find a group that works on phrase-lists and collects user submitted phrase-lists.

I've come across a few glype proxy sites that bypass content protection, and are obviously a nuisance.In my experience several key words such as “glype, unsensored, anonymous … ect”  are effective words to block these sites. 
 
Yes, Its worth being dedicated to purity and integrity on-line, so I would like to contribute, but don't know where to. 

-Jordy

---

### Post by roggan87 on 2011-04-12
> I have some experience on source-forge, administering a project that I created, so I would tend to lean towards that. It also let's each project have it's own forum too. As to ease of use, I understand that launchpad could auto build our .deb packages, whereas source-forge can't (to my knowledge). But, source-forge will let you use whatever versioning system you want, e.g. SVN git, Launchpad uses just bazzar. I prefer svn because there is a great tool called RabbitVCS that I like to use for versioning and it supports SVN.
And, sorry about just going ahead on the google group, I probably should have discussed it here first.

Okay, maybe we should use sourceforge then. Tetralectic is currently the only one (besides from mssever, but he isn't active) that has access to the project on sourceforge. Try to contact him to get privileges. I can also send you the older versions to upload them there as well.

> **Jordy_224 said:**
> Where can one find a group that works on phrase-lists and collects user submitted phrase-lists.

I've come across a few glype proxy sites that bypass content protection, and are obviously a nuisance.In my experience several key words such as “glype, unsensored, anonymous … ect”  are effective words to block these sites. 
 
Yes, Its worth being dedicated to purity and integrity on-line, so I would like to contribute, but don't know where to. 

-Jordy

Thanks for pointing out Jordy! Would you like to become an active blacklist-editor, or only to create one blacklist and make it public? If you only want to create one blacklist, then you can send me a private message with the keywords and I'll upload it.

---

### Post by mpnordland on 2011-04-12
Alright, I'll start on that.
I also concur that doing some tracking of wether proxies are used is good, but with so many tons of them, with diverse names, it may be very hard to be effective, and efficient. take a look here:  [http://proxy.org/](http://proxy.org/)

---

### Post by mpnordland on 2011-04-14
Here's what the gui will (hopefully) feature in the next version:
persistency: The gui will read the config file and load your username, and report settings. This is to avoid confusion.
Report settings: the gui will be able to edit what is sent in the report, and the attached report.

In the next next version I hope to add black and white list editing, but for now, I need to get this done and take a break

@roggan87: I'll need a way to upload the edited .conf to the website.

---

### Post by roggan87 on 2011-04-15
> **mpnordland said:**
> Here's what the gui will (hopefully) feature in the next version:
persistency: The gui will read the config file and load your username, and report settings. This is to avoid confusion.
Report settings: the gui will be able to edit what is sent in the report, and the attached report.

In the next next version I hope to add black and white list editing, but for now, I need to get this done and take a break

@roggan87: I'll need a way to upload the edited .conf to the website.

Ok, look at options in Python to send HTTP requests with POST variables. That's what we'll need.

Right now I'm doing something I should've done way back. I'm working on a forum that will be integrated with the website. It's an open source solution (SMF) that I'll try to tweak for our purposes. It will be as simplistic as possible, since we don't need a lot of features. The idea is to place questions, bug reports, feature requests, development information etc here but more divided. Then we can close this thread at Ubuntu Forums since it will be redundant.

---

### Post by mpnordland on 2011-04-15
I'll see to it. Please try to make sure the new forums have email alerts of new post to subscribed threads.

---

### Post by Jordy_224 on 2011-04-16
> **roggan87 said:**
> 
Thanks for pointing out Jordy! Would you like to become an active blacklist-editor, or only to create one blacklist and make it public? If you only want to create one blacklist, then you can send me a private message with the keywords and I'll upload it.



  Sure, sign me up for the blacklist editing group. I can contribute staring May during the weekends, but look for my keyword list posted soon.  

Thanks 



--Jordy

---

### Post by mpnordland on 2011-04-16
roggan87: what are the options for the attached report, specifically, the History, no history, and only hostnames

---

### Post by roggan87 on 2011-04-17
> **mpnordland said:**
> roggan87: what are the options for the attached report, specifically, the History, no history, and only hostnames

I'll work on email notification in the forum. Think it's a very important feature. Don't think it'll support PMs though, instead we'll have to work more with emailing each other in that case.

The options are history_paths or history_hostnames. If none of these values are present, no history will be shown.

---

### Post by mpnordland on 2011-04-18
We could just use phpBB, that's a pretty good opensource forum. One other thing, our new forum, How will we sign in? will we use our Net Responsibility accounts, or what?

---

### Post by mpnordland on 2011-04-18
Announcement: The GUI is now almost complete. I just need to do the upload the .conf thing. Once that is done I am going to devote my time to the multi-user branch, as that has been mostly ignored for a while now. I hope to be back hacking on the GUI next year. That should give me enough time to tie up all my loose ends.

---

### Post by roggan87 on 2011-04-20
> **mpnordland said:**
> We could just use phpBB, that's a pretty good opensource forum. One other thing, our new forum, How will we sign in? will we use our Net Responsibility accounts, or what?

Thanks for the suggestion, but I'll use [SMF]("http://simplemachines.org/"), another nice open source forum. We will use our Net Responsibility accounts. That's the tricky part to set up, but I've come pretty far. What do you think, should we use the username or real name in posts? There will be no such feature to view each others profile, but we have to show some sort of name, username och real name?

---

### Post by mpnordland on 2011-04-20
Mmm, Maybe that could be an option, but I would go for username as default.

---

### Post by sadastronaut on 2011-04-26
I recently downloaded Net Responsibility for Linux Mint, NR version 2.0.  I tried running the report, both through the GUI and command line.  Both times, it keeps cranking away, but never finishes the report, and I had to stop it both times.  I checked how much time it took last time (after I ctrl+c), and it was about 39,000 seconds.  Looking at my netresponsibility-log file, it's about 8.5 MB; not sure if that's unreasonable or not.  

I'm wondering if I've done something to flub things up.  Is there a way to kinda reset my settings or do an uninstall/reinstall?  Thanks.

---

### Post by roggan87 on 2011-04-27
> **sadastronaut said:**
> I recently downloaded Net Responsibility for Linux Mint, NR version 2.0.  I tried running the report, both through the GUI and command line.  Both times, it keeps cranking away, but never finishes the report, and I had to stop it both times.  I checked how much time it took last time (after I ctrl+c), and it was about 39,000 seconds.  Looking at my netresponsibility-log file, it's about 8.5 MB; not sure if that's unreasonable or not.  

I'm wondering if I've done something to flub things up.  Is there a way to kinda reset my settings or do an uninstall/reinstall?  Thanks.

I've sent you a PM about it.

---

### Post by sadastronaut on 2011-04-27
Thanks for the help earlier roggan.  I installed the 2.02 alpha version.  This is what I get when I try to run the test report.  
```

name@system ~ $ sudo net-responsibility-report 
Downloading the configurationfile...
Saving it.
net-responsibility-report[3100]: Generating report

Looking for bad keywords in the paths:
net-responsibility-report[3100]: Time for this report: 1.749971
net-responsibility-report[3100]: 
net-responsibility-report[3100]: Report Finished.
/usr/share/net-responsibility/lib/report.rb:173:in `full_report': undefined local variable or method `info' for #<Report:0xb77c6b74> (NameError)
    from /usr/share/net-responsibility/lib/report.rb:172:in `eval'
    from /usr/share/net-responsibility/lib/report.rb:173:in `full_report'
    from /usr/share/net-responsibility/lib/report.rb:172:in `each'
    from /usr/share/net-responsibility/lib/report.rb:172:in `full_report'
    from /usr/local/bin/net-responsibility-report:106:in `initialize'
    from /usr/local/bin/net-responsibility-report:150:in `new'
    from /usr/local/bin/net-responsibility-report:150

```

Any ideas?  I didn't have this problem with 2.0.  Thanks again to  you and others for all your work on this.

---

### Post by roggan87 on 2011-04-28
> **sadastronaut said:**
> Thanks for the help earlier roggan.  I installed the 2.02 alpha version.  This is what I get when I try to run the test report.  
```

name@system ~ $ sudo net-responsibility-report 
Downloading the configurationfile...
Saving it.
net-responsibility-report[3100]: Generating report

Looking for bad keywords in the paths:
net-responsibility-report[3100]: Time for this report: 1.749971
net-responsibility-report[3100]: 
net-responsibility-report[3100]: Report Finished.
/usr/share/net-responsibility/lib/report.rb:173:in `full_report': undefined local variable or method `info' for #<Report:0xb77c6b74> (NameError)
    from /usr/share/net-responsibility/lib/report.rb:172:in `eval'
    from /usr/share/net-responsibility/lib/report.rb:173:in `full_report'
    from /usr/share/net-responsibility/lib/report.rb:172:in `each'
    from /usr/share/net-responsibility/lib/report.rb:172:in `full_report'
    from /usr/local/bin/net-responsibility-report:106:in `initialize'
    from /usr/local/bin/net-responsibility-report:150:in `new'
    from /usr/local/bin/net-responsibility-report:150

```

Any ideas?  I didn't have this problem with 2.0.  Thanks again to  you and others for all your work on this.

Try to log in, look through your settings, save and log out. The report part "info" was a part of the 2.0 settings, but not anymore in 2.0.2.

Hope that works, let me know otherwise.

Roggan

---

### Post by sadastronaut on 2011-04-28
> **roggan87 said:**
> Try to log in, look through your settings, save and log out. The report part "info" was a part of the 2.0 settings, but not anymore in 2.0.2.

Hope that works, let me know otherwise.

Roggan

That worked.  Thanks!

---

### Post by Mickeyj4j on 2011-04-29
Personally i never found that net responsibility ever really gave out proper reports. well not like xxxchurch. its a shame that xxxchurch is only focusing on windows. their app is one of the best. also net responsibility is such a pain to install, and it is only working on Ubuntu, Ubuntu derivative such as Linux mint and possibly Debian (not to sure really). but if you could also port it for other linux os with source code that could be easily compiled it would be excellent.  also net responsibility needs better 64 bit support.

I hve not really used this for a long time because of the fact that it slowed down my computer to much even my 2.0mh dual core with 4gigs ram

---

### Post by roggan87 on 2011-04-29
> **Mickeyj4j said:**
> Personally i never found that net responsibility ever really gave out proper reports. well not like xxxchurch. its a shame that xxxchurch is only focusing on windows. their app is one of the best. also net responsibility is such a pain to install, and it is only working on Ubuntu, Ubuntu derivative such as Linux mint and possibly Debian (not to sure really). but if you could also port it for other linux os with source code that could be easily compiled it would be excellent.  also net responsibility needs better 64 bit support.

I hve not really used this for a long time because of the fact that it slowed down my computer to much even my 2.0mh dual core with 4gigs ram

We're doing the best we can, welcome to contribute. If you haven't tried it for a long time, you should go ahead and install it again, 2.0.2 is way much faster than earlier versions. I also think the reports are getting better.

Is it any specific Linux distribution you're thinking of? I agree it would be nice to have an easier installation for all kind of platforms.

Please remember we're all doing this voluntarily, in our spear time, without getting paid. We're not even professionals.

If you really want to help us, then either try to convince some really good programmer to join us in the development, or at least come with some constructive feedback. What do you like better with the x3watch reports? What do you not like with the Net Responsibility reports? How can we make them better?

I think (without promising too much) I'll dig into the project to rewrite the code from scratch in another language (c++) to make it more platform-independent and faster. This might take a long time though, not sure how many months or years...

If you don't like Net Responsibility, you don't have to use it. I do hope though that you'll find it a little helpful in some way ;)

Roggan

---

### Post by mpnordland on 2011-04-29
In this line of conversation, because of my dislike of unity, I am now running opensuse I'm working on building the rpm for my (x64) system, and once I get it right, I'll upload them here.
I just tried those packages that roggan87 uploaded, and they seemed to work, except for the fact that I had yast running, So, I'll report back if they do in deed work, then I'll build the 2.0.2 alphas and test them.

---

### Post by mpnordland on 2011-04-30
Ok, I'm still trying to install, there are still some problems with dependancies, and I can't run the configure packages for some reason. 
wxPython is different, and I can't seem to find dsniff on the web. I'm still trying, because I *know* It's possible! :)

---

### Post by mpnordland on 2011-04-30
python-wxWidgets is wxPython in Opensuse 11.4, could you perhaps make me a package with that as the wxPython dependancy please? I think I can get everything else.

---

### Post by roggan87 on 2011-05-01
I'll try to compile a new RPM-package as soon as possible, but I can't really promise when that is.

I think the forum is shaping up. You can try it out if you want, [www.netresponsibility.com/forum](www.netresponsibility.com/forum). It's not released, and it's not completely functional yet, but on its way. You can log in with your regular accounts and the notification should work as well. Feel free to fill it up with useful info right away! Please report bugs or any other things you might run into. The layout is not 100% satisfying, but I'm working on it...
Some of you are already set as moderators on the board, the same that are admins on the website. If you have a tab called "Edit Help", you're an admin. You'll have a lot of more options, otherwise not shown to regular users. Just letting you know...
The intention of the forum is not to be a big flashy forum competing with other social medias, but rather to be a place to talk, get and give help about Net Responsibility.
The board General Category is full of rubbish at the moment, I'll delete that ;)

All for now,
Roggan

---

### Post by mpnordland on 2011-05-02
The forum looks great! It seems to be just what we need and nothing more. I'll try to run the configure-packages again, because right now I'm running with out net responsibility, which is not a good thing.

---

### Post by mpnordland on 2011-05-02
I did some brute forcing of packages, and I got it installed. I started the daemon manually, cause it didn't start when it installed, and that didn't give errors, but when running a test mail, this came out:
```
sh: ifconfig: command not found
/usr/share/net-responsibility/lib/options.rb:181:in `get_mac': private method `gsub' called for nil:NilClass (NoMethodError)
	from /usr/share/net-responsibility/lib/options.rb:180:in `popen'
	from /usr/share/net-responsibility/lib/options.rb:180:in `get_mac'
	from /usr/share/net-responsibility/lib/options.rb:77:in `set_options'
	from /usr/share/net-responsibility/lib/options.rb:36:in `initialize'
	from /usr/local/bin/net-responsibility-report:94:in `new'
	from /usr/local/bin/net-responsibility-report:94:in `initialize'
	from /usr/local/bin/net-responsibility-report:151:in `new'
	from /usr/local/bin/net-responsibility-report:151
```
A regular report appeared in my inbox although I don't know if that is because of it being time to send a report or not. And the test mail never showed.

---

### Post by roggan87 on 2011-05-03
> **mpnordland said:**
> I did some brute forcing of packages, and I got it installed. I started the daemon manually, cause it didn't start when it installed, and that didn't give errors, but when running a test mail, this came out:
```
sh: ifconfig: command not found
/usr/share/net-responsibility/lib/options.rb:181:in `get_mac': private method `gsub' called for nil:NilClass (NoMethodError)
	from /usr/share/net-responsibility/lib/options.rb:180:in `popen'
	from /usr/share/net-responsibility/lib/options.rb:180:in `get_mac'
	from /usr/share/net-responsibility/lib/options.rb:77:in `set_options'
	from /usr/share/net-responsibility/lib/options.rb:36:in `initialize'
	from /usr/local/bin/net-responsibility-report:94:in `new'
	from /usr/local/bin/net-responsibility-report:94:in `initialize'
	from /usr/local/bin/net-responsibility-report:151:in `new'
	from /usr/local/bin/net-responsibility-report:151
```
A regular report appeared in my inbox although I don't know if that is because of it being time to send a report or not. And the test mail never showed.

The problem is that you'll have to run *ifconfig*. Either you didn't runt Net Responsibility as root, or you'll have to install further packages. Look at this topic: [http://forums.opensuse.org/archives/sf-archives/archives-network-internet/324821-where-ifconfig-iwconfig.html](http://forums.opensuse.org/archives/sf-archives/archives-network-internet/324821-where-ifconfig-iwconfig.html)
When you get ifconfig working, please try the daemon again.

---

### Post by mpnordland on 2011-05-03
Both those work flawlessly, I figured out that I needed libpcap installed, so I found and installed that. I've uninstalled and I'm going to reinstall to try it now.
Ok, here's the out put:

```
linux-f2ld:/home/micah/Downloads # rpm -ihv ./netresponsibility-2.0.amd64-alternative.rpm 
Preparing...                ########################################### [100%]
   1:netresponsibility      ########################################### [100%]
gtk-update-icon-cache -f /usr/share/icons/hicolor
gtk-update-icon-cache: Cache file created successfully.
Setting up init scripts...
/etc/software/init.d/net-responsibility-daemon: line 45: log_daemon_msg: command not found
/etc/init.d/net-responsibility-daemon: Starting net-responsibility-daemon
/etc/software/init.d/net-responsibility-daemon: line 48: log_end_msg: command not found

```

---

### Post by mpnordland on 2011-05-03
running the report with su worked great, now, I moved on to testing the daemon this is the output I get:

```
linux-f2ld:/home/micah # net-responsibility-daemon --nodaemon
net-responsibility-daemon[10968]: Starting
net-responsibility-report[10978]: Generating report
net-responsibility-report[10978]: Sending report
net-responsibility-report[10978]: Rotating log
net-responsibility-report[10978]: Time for this report: 3.511011
net-responsibility-report[10978]: 
net-responsibility-report[10978]: Report Finished.
/usr/lib64/ruby/gems/1.8/gems/sqlite3-ruby-1.3.0/lib/sqlite3/database.rb:83:in `initialize': near "OR": syntax error (SQLite3::SQLException)
	from /usr/lib64/ruby/gems/1.8/gems/sqlite3-ruby-1.3.0/lib/sqlite3/database.rb:83:in `new'
	from /usr/lib64/ruby/gems/1.8/gems/sqlite3-ruby-1.3.0/lib/sqlite3/database.rb:83:in `prepare'
	from /usr/lib64/ruby/gems/1.8/gems/sqlite3-ruby-1.3.0/lib/sqlite3/database.rb:257:in `query'
	from /usr/share/net-responsibility/lib/modules/db.rb:158:in `rotate_log'
	from /usr/share/net-responsibility/lib/../net-responsibility-report:122:in `initialize'
	from /usr/share/net-responsibility/lib/../net-responsibility-report:151:in `new'
	from /usr/share/net-responsibility/lib/../net-responsibility-report:151
net-responsibility-daemon[10968]: Caught interrupt. Exiting.
```
Two other things, ```
urlsnarf -i all
``` doesn't work, and ```
urlsnarf -i wlan0
``` produces nothing.

---

### Post by sadastronaut on 2011-05-03
> **roggan87 said:**
> We're doing the best we can, welcome to contribute. If you haven't tried it for a long time, you should go ahead and install it again, 2.0.2 is way much faster than earlier versions. I also think the reports are getting better.

Is it any specific Linux distribution you're thinking of? I agree it would be nice to have an easier installation for all kind of platforms.

Please remember we're all doing this voluntarily, in our spear time, without getting paid. We're not even professionals.

If you really want to help us, then either try to convince some really good programmer to join us in the development, or at least come with some constructive feedback. What do you like better with the x3watch reports? What do you not like with the Net Responsibility reports? How can we make them better?

I think (without promising too much) I'll dig into the project to rewrite the code from scratch in another language (c++) to make it more platform-independent and faster. This might take a long time though, not sure how many months or years...

If you don't like Net Responsibility, you don't have to use it. I do hope though that you'll find it a little helpful in some way ;)

Roggan

Not making any promises, but if you do port it to C++ I may be able to help once that's done.  I know C++ but not Ruby.

---

### Post by sadastronaut on 2011-05-03
> **roggan87 said:**
> We're doing the best we can, welcome to contribute. If you haven't tried it for a long time, you should go ahead and install it again, 2.0.2 is way much faster than earlier versions. I also think the reports are getting better.

Is it any specific Linux distribution you're thinking of? I agree it would be nice to have an easier installation for all kind of platforms.

Please remember we're all doing this voluntarily, in our spear time, without getting paid. We're not even professionals.

If you really want to help us, then either try to convince some really good programmer to join us in the development, or at least come with some constructive feedback. What do you like better with the x3watch reports? What do you not like with the Net Responsibility reports? How can we make them better?

I think (without promising too much) I'll dig into the project to rewrite the code from scratch in another language (c++) to make it more platform-independent and faster. This might take a long time though, not sure how many months or years...

If you don't like Net Responsibility, you don't have to use it. I do hope though that you'll find it a little helpful in some way ;)

Roggan

I can't speak for previous versions, but I'm running 2.02a. I had a couple issues but roggan helped me out.  Now it's running great, and it's running on a 5 year old computer.  

Concerning the reports, the gold standard that I know of is Covenant Eyes.  NetResponsibility isn't quite there yet, but in my view, NR provides the essential ingredient of keeping my surfing habits out in the open.  For me, just knowing that my surfing habits are being logged is enough to keep me accountable.  I understand different people are at different stages, and that's something to consider when pondering Linux in the first place.

Edit to Add:  That being said, I think the reports are pretty good so far, at least in my limited experience of using it.  My point was that accountability/transparency is primary.

---

### Post by marech on 2011-05-04
i tried to install NR ([netresponsibility-2.0.2.amd64.deb]("http://www.netresponsibility.com/files/netresponsibility-2.0.2.amd64.deb")), but get a bug (see attached file) and when i tried to get a testmail 
 
sudo net-responsibility-report --testmail

i got

[INDENT] [B]/usr/share/net-responsibility/lib/options.rb:181:in `get_mac': private method `gsub' called for nil:NilClass (NoMethodError)
    from /usr/share/net-responsibility/lib/options.rb:180:in `popen'
    from /usr/share/net-responsibility/lib/options.rb:180:in `get_mac'
    from /usr/share/net-responsibility/lib/options.rb:77:in `set_options'
    from /usr/share/net-responsibility/lib/options.rb:36:in `initialize'
    from /usr/local/bin/net-responsibility-report:94:in `new'
    from /usr/local/bin/net-responsibility-report:94:in `initialize'
    from /usr/local/bin/net-responsibility-report:150:in `new'
    from /usr/local/bin/net-responsibility-report:150
[/B][/INDENT]my system: ubuntu 10.4 / 64bit

how can i fix this errors, i read the forum, but didn't get the point.

thanx for your support!

---

### Post by roggan87 on 2011-05-05
> **marech said:**
> i tried to install NR ([netresponsibility-2.0.2.amd64.deb]("http://www.netresponsibility.com/files/netresponsibility-2.0.2.amd64.deb")), but get a bug (see attached file) and when i tried to get a testmail 
 
sudo net-responsibility-report --testmail

i got

[INDENT] [B]/usr/share/net-responsibility/lib/options.rb:181:in `get_mac': private method `gsub' called for nil:NilClass (NoMethodError)
    from /usr/share/net-responsibility/lib/options.rb:180:in `popen'
    from /usr/share/net-responsibility/lib/options.rb:180:in `get_mac'
    from /usr/share/net-responsibility/lib/options.rb:77:in `set_options'
    from /usr/share/net-responsibility/lib/options.rb:36:in `initialize'
    from /usr/local/bin/net-responsibility-report:94:in `new'
    from /usr/local/bin/net-responsibility-report:94:in `initialize'
    from /usr/local/bin/net-responsibility-report:150:in `new'
    from /usr/local/bin/net-responsibility-report:150
[/B][/INDENT]my system: ubuntu 10.4 / 64bit

how can i fix this errors, i read the forum, but didn't get the point.

thanx for your support!

Hi!

I'm sorry to say you're not the first one experience this problem. I'll try to help you as soon as possible.

Robert

---

### Post by Mickeyj4j on 2011-05-15
Hi i am wondering how often reports are generated i have sent reports also to my email address to test but nothing much comes thru.    

also does using private browsing in a browser also hidden from reports

---

### Post by roggan87 on 2011-05-15
> **Mickeyj4j said:**
> Hi i am wondering how often reports are generated i have sent reports also to my email address to test but nothing much comes thru.    

also does using private browsing in a browser also hidden from reports

Hi Mickeyj4j!

You can set up how often the reports should be sent out. By default it's every 7th day. If you log in on the website, the field called "Report Frequency" decides how often they're generated. If no reports are automatically generated, you can try to set up cron as shortly described here: [http://netresponsibility.com/help.php#80]("http://netresponsibility.com/help.php#80")
You can also send reports manually by opening a terminal and running this command:
```
sudo net-responsibility-report
```

Net Responsibility will log all history, even if using private browsing, incognito mode, or any other way.

Good luck!

---

### Post by Jordy_224 on 2011-05-15
> **Jordy_224 said:**
> ...I've come across a few glype proxy sites that bypass content protection, and are obviously a nuisance.In my experience several key words such as &#8220;glype, unsensored, anonymous &#8230; ect&#8221;  are effective words to block these sites. 



So, I wrote a program, to return a list of keywords, that are most prevalent in proxy sites. A total of 250 glype and php proxy sites were searched.  The results are shown in the attached file. The first column shows the count and the second shows the keyword. I found that &#8220;Proxy", "encodeURL", "Glype&#8221; words occur more often than &#8220;uncensored", "webproxy" and "unrestricted&#8221;. Also, many of the keywords are case-sensitive. 

I "dream" of one-day designing the "perfect" bannedsite_phrase list (no FP). If one exists.
 
-Jordy

---

### Post by Mickeyj4j on 2011-05-16
> **roggan87 said:**
> Hi Mickeyj4j!

You can set up how often the reports should be sent out. By default it's every 7th day. If you log in on the website, the field called "Report Frequency" decides how often they're generated. If no reports are automatically generated, you can try to set up cron as shortly described here: [http://netresponsibility.com/help.php#80]("http://netresponsibility.com/help.php#80")
You can also send reports manually by opening a terminal and running this command:
```
sudo net-responsibility-report
```

Net Responsibility will log all history, even if using private browsing, incognito mode, or any other way.

Good luck!

thanks how do i actually achieve editing this profile it deffinatly is not sending reports at all even with the default 7 days

---

### Post by Mickeyj4j on 2011-05-16
another thing i want to know is if i am running another os in a virtual machine such as vbox or vmwhere etc will net responsibility log all Internet information accessed from the vbox install.  just wondering as to weather i am needing to install net responsability again or for windows xxxchunch.   

for any other linux os running can i point to the folders on the ubuntu host os adn use them or will that only work for ubuntu or debian baised os 
or not at all

---

### Post by mpnordland on 2011-05-16
> **Jordy_224 said:**
> So, I wrote a program, to return a list of keywords, that are most prevalent in proxy sites. A total of 250 glype and php proxy sites were searched.  The results are shown in the attached file. The first column shows the count and the second shows the keyword. I found that &#8220;Proxy", "encodeURL", "Glype&#8221; words occur more often than &#8220;uncensored", "webproxy" and "unrestricted&#8221;. Also, many of the keywords are case-sensitive. 

I "dream" of one-day designing the "perfect" bannedsite_phrase list (no FP). If one exists.
 
-Jordy

Wow! That's a great list. With something like that, maybe we could add an alert to the report if a web proxy seems to be in use (i.e. one of those keywords is found). Also, since you've included the frequencies of occurrence, We could assign "weight" to the words so that we could gauge how likely it was that a proxy was being used.
Once again, that's a great list!

---

### Post by roggan87 on 2011-05-16
> So, I wrote a program, to return a list of keywords, that are most prevalent in proxy sites. A total of 250 glype and php proxy sites were searched. The results are shown in the attached file. The first column shows the count and the second shows the keyword. I found that “Proxy", "encodeURL", "Glype” words occur more often than “uncensored", "webproxy" and "unrestricted”. Also, many of the keywords are case-sensitive. 

I "dream" of one-day designing the "perfect" bannedsite_phrase list (no FP). If one exists.

-Jordy

I've looked at your blacklist, and it looks good! I'll try to upload it in the near future. Some words will not be included (such as name, text etc...) and some words will be modified. I'll do the best I can with it.
I'd also be interested in getting the program you wrote, it might become useful in the future.

> **Mickeyj4j said:**
> thanks how do i actually achieve editing this profile it deffinatly is not sending reports at all even with the default 7 days

You go to [www.netresponsibility.com/login.php]("http://www.netresponsibility.com/login.php"), log in, open the title "Tweaks" in the configurations, set "Report Frequency" to how many days you want between each report, go to the bottom, click "Log out", enter the security code, click "Save and log out". Then your settings should be changed. Did it work to send reports manually, with net-responsibility-report?

> another thing i want to know is if i am running another os in a virtual machine such as vbox or vmwhere etc will net responsibility log all Internet information accessed from the vbox install. just wondering as to weather i am needing to install net responsability again or for windows xxxchunch. 

for any other linux os running can i point to the folders on the ubuntu host os adn use them or will that only work for ubuntu or debian baised os or not at all

I'm not sure about the vbox thing. Do you mean if you're running another os inside vbox on a Linux machine that has Net Responsibility installed?

It might be a little trickier to get Net Responsibility installed on Linux-distros that are not debianbased, because the dependencies are quite different. It depends on what distro you have in mind. Any particular?

> Wow! That's a great list. With something like that, maybe we could add an alert to the report if a web proxy seems to be in use (i.e. one of those keywords is found). Also, since you've included the frequencies of occurrence, We could assign "weight" to the words so that we could gauge how likely it was that a proxy was being used.
Once again, that's a great list!

Since I'm currently trying to rewrite Net Responsibility in C++ (and have come quite a bit) it will be easier to implement that feature. The keywords will have individual "strength" to improve the matching results. Matches will then be graded... In the attached reports, one will have the opportunity to rank every match, which will help us develop the blacklists even further (or update them automatically).

Right now I have written a sniffer, filter, options loading and database support (in C++). That means I have a program that updates blacklists and configfile if modified, sniffing the network for all URLs, filtering them and storing them in the database. That's most of the daemon, I only have to make it a daemon/service. I haven't started with the report related part yet, but I think that will be easier. The idea is to make the software open for modules (especially report modules) so others can develop their own report template. That will help people to get satisfied with the reports (since one can choose between different), and it'll be easier to help out in developing those.

Ok, long post, but that's it for now,
God bless!

---

### Post by mpnordland on 2011-05-16
If we now have our own sniffer, then maybe I should just bite the bullet, and write a proxy. It would be a good project to finally really launch me into c++. Should I write it as a module? Is there a spec for such a thing?
On another note, I now have access to the net responsibility project on sourceforge, so I'll get the latest released source in trunk, I'll set up a branch for the c++ rewrite that you can use. pm me with your sourceforge name and I'll see what I can do to get it setup.

---

### Post by roggan87 on 2011-05-18
> **mpnordland said:**
> If we now have our own sniffer, then maybe I should just bite the bullet, and write a proxy. It would be a good project to finally really launch me into c++. Should I write it as a module? Is there a spec for such a thing?
On another note, I now have access to the net responsibility project on sourceforge, so I'll get the latest released source in trunk, I'll set up a branch for the c++ rewrite that you can use. pm me with your sourceforge name and I'll see what I can do to get it setup.

That's exactly what I think would be the next step! If we would have our own transparent proxy, then we wouldn't need to depend on libpcap/winpcap, and we would also have the ability to block certain sites (optionally), and it would be even faster, and we could also have a similar feature as Covenant Eyes' Panic button. [http://www.covenanteyes.com/services/accountability/feature-tour/]("http://www.covenanteyes.com/services/accountability/feature-tour/"), that would block all internet access at critical periods, until one accountability partner "restores" the access.

So, it would open up a lot of new possibilities. Please go ahead and bite the bullet! I don't think you have to write it as a module, at least not yet. Some guidelines you can try to follow is found here: [http://geosoft.no/development/cppstyle.html#introduction]("http://geosoft.no/development/cppstyle.html#introduction"). I've tried to follow those guidelines.

Right now, I've used a lot of the [POCO Library]("http://www.pocoproject.org"). There you have support for Regular Expressions, a lot of network functions etc, and it's cross-platform. Try to write as much as possible cross-platform.
I also intend to use QT as GUI, since it has native support for Windows, Mac OS X, KDE and Unity (maybe Gnome as well). They also support some functionality for Proxies ([Look here]("http://web.mit.edu/qt-dynamic/www/qnetworkproxy.html"))
Right now, I've only compiled the code on a windows machine, using MinGW (GNU GCC), but it shouldn't be hard to get going on a Linux box as well.

To sum up, all you need to do, is to write a transparent proxy that sniffs all GET reguests, and returns the pages that were requested. Then I could easily implement the filtering and other stuff into that code.

Thanks Micah!
Blessings

---

### Post by roggan87 on 2011-05-18
@Micah
About SourceForge: Please add a branch. I've been added to the project as well (roggan87), but I don't seem to have any access to change settings like website or any other settings. I'll contact Mssever about that.

---

### Post by mpnordland on 2011-05-19
for the moment, I'm having trouble with the svn, but once I've gotten that resolved, I'll get that setup and tell you. I've been looking at the POCO libraries, and they seem perfect for our purpose. I don't know much about writing cross platform code in C++, as I'm really just starting, but I will do my best. On a second note, I think that if we are to have a modular architecture, We should just implement a daemon, and then let everything else be modules. Reporting, Logging, Sniffing, could all be replaceable. We would have our set of modules which we would develop and support. That would make it a much more flexible system. As for Qt, I guess that would be alright, I'm just really attached to wxPython! :) I think we should at least keep the gui in python, because trying to maintain a gui in C++ I hear is really hard. Qt has python bindings, so we should be good there.

---

### Post by roggan87 on 2011-05-19
> **mpnordland said:**
> for the moment, I'm having trouble with the svn, but once I've gotten that resolved, I'll get that setup and tell you. I've been looking at the POCO libraries, and they seem perfect for our purpose. I don't know much about writing cross platform code in C++, as I'm really just starting, but I will do my best. On a second note, I think that if we are to have a modular architecture, We should just implement a daemon, and then let everything else be modules. Reporting, Logging, Sniffing, could all be replaceable. We would have our set of modules which we would develop and support. That would make it a much more flexible system. As for Qt, I guess that would be alright, I'm just really attached to wxPython! :) I think we should at least keep the gui in python, because trying to maintain a gui in C++ I hear is really hard. Qt has python bindings, so we should be good there.

I'm also a bit of a starter in c++ programming, though I've used a lot of c++ like syntax in other scripting languages, such as PHP and JavaScript. I like the idea of modular architecture, but I'm not 100% sure of how to think "modular". Right now the main file looks like this:
```
#include <iostream>

#include "Options.h"
#include "Filter.h"
#include "Database.h"
#include "Sniffer.h"

using namespace std;

int main(int argc, char* argv[])
{
	Options options(argc, argv);
	Filter filter(options);
	Database db(options);
	Sniffer sniffer(filter, db, options);
	sniffer.startLoop();
	return 0;
}

```
I think it should be pretty easy to make it more modular from there. Any help is of course welcome!

One important perspective to remember is to make NR configurable but still prevent the user from circumventing it.

Regarding the GUI in Python, I guess that's alright for now. In that case I think we can stick to wxPython. The GUI is not the most important part in this rewriting of code, but in the end, I'd really like to see this whole project in c++ only. The reason is that most Windows and Mac machines doesn't have Python installed, and it feels redundant to have to depend on that. BUT, I will not dive into GUI programming before the other pieces of software feels good enough. Therefore we can still use the GUI you've created ;) Micah - Robert: 1-0.

Take care!
Robert

---

### Post by mpnordland on 2011-05-19
Actually, thanks to the magic of py2exe we can make a "binary" of a python app for windows\\:D/, and as for mac, well mac includes python, or we could use py2app. Another question: does anyone here have a mac that we could compile on?
Also, I've gotten setup with POCO, it was a pain in the neck, as I had to compile, and then manually put the shared libs where they were supposed to go, but I got it working now. It looks as if the Sniffer class is doing all the work, it maybe a good idea to move that some where else, so that the daemon is handling passing the urls through the filter to the database. That would make it easier to create modules that seamlessly interact with each other, even though they weren't specifically designed to work together. I'm sort of floundering as to where to start on the proxy, but I've gotten a good look at C++'s syntax, and I'll be moving forward. I really need to figure out what classes to use to open a port, and to start listening. Once I've gotten that working, I'll be in a good position to finish.

---

### Post by roggan87 on 2011-05-19
> **mpnordland said:**
> Actually, thanks to the magic of py2exe we can make a "binary" of a python app for windows\\:D/, and as for mac, well mac includes python, or we could use py2app. Another question: does anyone here have a mac that we could compile on?
Also, I've gotten setup with POCO, it was a pain in the neck, as I had to compile, and then manually put the shared libs where they were supposed to go, but I got it working now. It looks as if the Sniffer class is doing all the work, it maybe a good idea to move that some where else, so that the daemon is handling passing the urls through the filter to the database. That would make it easier to create modules that seamlessly interact with each other, even though they weren't specifically designed to work together. I'm sort of floundering as to where to start on the proxy, but I've gotten a good look at C++'s syntax, and I'll be moving forward. I really need to figure out what classes to use to open a port, and to start listening. Once I've gotten that working, I'll be in a good position to finish.

Thanks for that useful info :) Sounds good in my ears.
I see what you mean with the Sniffer class. We can think about how to restructure that. For the moment I'm working on the reports and generating them. Have successfully sent a couple of reports, but I still have to format them. I'm really excited about this, the sniffing and filtering is waaay much faster than in Ruby! I also like this modular thinking, I see a lot of possibilities. It's really good to have you in this project Micah, I appreciate all you've done so far, and will be doing!

---

### Post by muppett on 2011-05-20
I've just installed netresponsibility 2.0 but am getting the following error when trying to send a test email.

any help would be appreciated.

```
/usr/lib/ruby/1.8/yaml.rb:133:in `load': syntax error on line 6, col 3: `	- adult' (ArgumentError)
	from /usr/lib/ruby/1.8/yaml.rb:133:in `load'
	from /usr/share/net-responsibility/lib/server_connection.rb:53:in `get_blacklists'
	from /usr/share/net-responsibility/lib/options.rb:217:in `update_settings'
	from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
	from /usr/local/bin/net-responsibility-report:94:in `new'
	from /usr/local/bin/net-responsibility-report:94:in `initialize'
	from /usr/local/bin/net-responsibility-report:151:in `new'
	from /usr/local/bin/net-responsibility-report:151

```

---

### Post by roggan87 on 2011-05-22
> **muppett said:**
> I've just installed netresponsibility 2.0 but am getting the following error when trying to send a test email.

any help would be appreciated.

```
/usr/lib/ruby/1.8/yaml.rb:133:in `load': syntax error on line 6, col 3: `	- adult' (ArgumentError)
	from /usr/lib/ruby/1.8/yaml.rb:133:in `load'
	from /usr/share/net-responsibility/lib/server_connection.rb:53:in `get_blacklists'
	from /usr/share/net-responsibility/lib/options.rb:217:in `update_settings'
	from /usr/share/net-responsibility/lib/options.rb:38:in `initialize'
	from /usr/local/bin/net-responsibility-report:94:in `new'
	from /usr/local/bin/net-responsibility-report:94:in `initialize'
	from /usr/local/bin/net-responsibility-report:151:in `new'
	from /usr/local/bin/net-responsibility-report:151

```

Hi!

Delete /usr/share/net-responsibility/lib/lists.lst and try again. Get back here if it still doesn't work.

Robert

---

### Post by muppett on 2011-05-22
Thanks for the reply.

I deleted the file and tried again, but still getting the same error.

---

### Post by thejambi on 2011-05-23
> **muppett said:**
> Thanks for the reply.

I deleted the file and tried again, but still getting the same error.

Hey guys. Just installed as well and get the same as above. 

Also, could someone point me to the repository info, etc for this project? I am interested in getting involved.

---

### Post by mpnordland on 2011-05-23
@thejambi: We are currently in the midst of a complete rewrite. Any help would be appreciated. Our code is hosted at [www.sourceforge.net/projects/responsibility](www.sourceforge.net/projects/responsibility) I should have a branch created for our new rewrite by at least next week. I just got my problems with the svn fixed today, and I'm going on a trip tommorow, so I don't know if I'll get much done then. If you know C++ you can help. Even if you don't and are willing to learn, you can still help. Doing this is a learning experience for both roggan87 and me. See [this]("http://ubuntuforums.org/showpost.php?p=10830808&postcount=762") post for more information on how we are doing things.
@roggan87: As I said above, I got my problems with the svn worked out, and I'll try to get that branch up by next week, or if you're feeling brave, just do it yourself, it's not that hard :D

---

### Post by roggan87 on 2011-05-24
> **thejambi said:**
> Hey guys. Just installed as well and get the same as above. 

Also, could someone point me to the repository info, etc for this project? I am interested in getting involved.

It was a bug on the website, but it should be fixed now. If it doesn't work, delete /usr/share/net-responsibility/lib/lists.lst and try again. Let me know if you run into more problems.

Robert

---

### Post by thejambi on 2011-05-24
> **roggan87 said:**
> It was a bug on the website, but it should be fixed now. If it doesn't work, delete /usr/share/net-responsibility/lib/lists.lst and try again. Let me know if you run into more problems.

Robert
Awesome. Worked after deleting the mentioned lists file. Thanks!

---

### Post by Mickeyj4j on 2011-05-30
> **roggan87 said:**
> Hi Mickeyj4j!

You can set up how often the reports should be sent out. By default it's every 7th day. If you log in on the website, the field called "Report Frequency" decides how often they're generated. If no reports are automatically generated, you can try to set up cron as shortly described here: [http://netresponsibility.com/help.php#80]("http://netresponsibility.com/help.php#80")
You can also send reports manually by opening a terminal and running this command:
```
sudo net-responsibility-report
```

Net Responsibility will log all history, even if using private browsing, incognito mode, or any other way.

Good luck!

well it does not log anything and send emails, i have left default values selected i am sure. i also send reports to myself without any luck this is how i know its working or not 
all i get is replies from this forum from time to time.

---

### Post by mpnordland on 2011-05-30
Hey guys, I've got the branch created, It's located at: [https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/C++_Rewrite/](https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/C++_Rewrite/) . That url should also work with a svn client. I personally recommend [RabbitVCS]("http://www.rabbitvcs.org/"), as it allows you to work with the svn in nautilus or thunar. On windows, [TortiseSVN]("http://tortoisesvn.net/") does the same.
Note: RabbitVCS does not yet work with Gnome 3

---

### Post by mpnordland on 2011-05-31
Praise God from Whom proxies flow! After struggling with it for all of last week and yesterday, I've finally created a proxy! You can find my work along with a pre-built, not-entirely-sure-to-work-on-your-system 64bit binary in the C++ branch(look under /branches/C++_rewrite/proxy/net-responsibility-proxy/bin/debug for the binary). You can also build your own along with the included Code::Blocks project file. Code::Blocks is available from the Ubuntu repos.
Till next time,
Micah

---

### Post by roggan87 on 2011-06-01
> **Mickeyj4j said:**
> well it does not log anything and send emails, i have left default values selected i am sure. i also send reports to myself without any luck this is how i know its working or not 
all i get is replies from this forum from time to time.

Mickeyj4j, in order to help you I need to get more information on what's going wrong. Try these commands and tell me the output on each of them:

```
sudo net-responsibility-config-cli
ps -ef|grep net-responsibility
sudo net-responsibility-daemon --nodaemon
sudo net-responsibility-report
sudo net-responsibility-report --testmail
```

What distribution are you using, and which version?
Thanks.

@Micah: You're a genius! I could compile it on my windows machine (unfortunately stuck to it), but I never managed to establish any connection. I'm not very familiar with proxies, so any help would be appreciated here. I can still use internet as before, but without any communication with the proxy I guess.

I've taken a look at the SVN branch, looks perfect. Also installed TortoiseSVN, and it runs like a charm. Now we're ready to go! My code is still only tested on Windows, but with a little tweaking it should work on Linux as well.

Roggan

---

### Post by mpnordland on 2011-06-01
Well, in chrome, you can use this link to change your proxy settings:[chrome://settings/search#proxy]("chrome://settings/search#proxy") In Firefox 4 go to the Firefox menu, choose preferences> preferences > advanced > network > settings. In either one choose manual proxy, type "localhost" after "HTTP proxy". The port number is 9980. Also, don't set it up as the system proxy, It will probably mess a lot of stuff up. Some websites are really broken with it, try stackoverflow for a good example. But for the most part, it works alright. If you run it in the Command prompt (or terminal), it will output all the hostnames you access. I could have it do more, but I just haven't done it yet. The POCO libraries were most helpful. Right now I want to get it working with all websites, but once that's done, I will move on to making it a module. We need to have a specification for how we will integrate things. Once you get your code up on the svn I'll see how it compiles, and then start thinking of ways to make it all modular.
As for the Windows machine, Virtualbox is a very good virtual machine, I use it to test new Ubuntu versions and run Windows programs occasionally. You can find it at [http://www.virtualbox.org/]("http://www.virtualbox.org/").

---

### Post by roggan87 on 2011-06-01
> **mpnordland said:**
> Well, in chrome, you can use this link to change your proxy settings:[chrome://settings/search#proxy]("chrome://settings/search#proxy") In Firefox 4 go to the Firefox menu, choose preferences> preferences > advanced > network > settings. In either one choose manual proxy, type "localhost" after "HTTP proxy". The port number is 9980. Also, don't set it up as the system proxy, It will probably mess a lot of stuff up. Some websites are really broken with it, try stackoverflow for a good example. But for the most part, it works alright. If you run it in the Command prompt (or terminal), it will output all the hostnames you access. I could have it do more, but I just haven't done it yet. The POCO libraries were most helpful. Right now I want to get it working with all websites, but once that's done, I will move on to making it a module. We need to have a specification for how we will integrate things. Once you get your code up on the svn I'll see how it compiles, and then start thinking of ways to make it all modular.
As for the Windows machine, Virtualbox is a very good virtual machine, I use it to test new Ubuntu versions and run Windows programs occasionally. You can find it at [http://www.virtualbox.org/]("http://www.virtualbox.org/").

Thanks!
Sorry, but after some research I found out how to set it up. As you said, some websites are messed up, any idea why? Before we release this rewrite (in other words no hurry) we have to make this proxy work regardless of individual proxy settings in the browsers. Is that possible, what do you think? Otherwise it would loose it's meaning. I don't mean to criticize, only point out.

Ok, I'll upload the code as is, without guaranties ;)
It's now available at [https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/C++_Rewrite/dev/](https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/C++_Rewrite/dev/)

---

### Post by mpnordland on 2011-06-01
Great, I'll look at it later, One possible reason may be that I'm right now not passing along the user-agent, the other maybe that I'm not making any difference between content types. I'm going to go over what I have and try to implement it in a better, more comprehensive way. By the way, do you use Code::Blocks too?

---

### Post by sadastronaut on 2011-06-01
> **roggan87 said:**
> Thanks!
Sorry, but after some research I found out how to set it up. As you said, some websites are messed up, any idea why? Before we release this rewrite (in other words no hurry) we have to make this proxy work regardless of individual proxy settings in the browsers. Is that possible, what do you think? Otherwise it would loose it's meaning. I don't mean to criticize, only point out.

Ok, I'll upload the code as is, without guaranties ;)
It's now available at [https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/C++_Rewrite/dev/](https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/C++_Rewrite/dev/)

Is it possible to block access via the local port, so that browsing has to happen via a proxy?

---

### Post by roggan87 on 2011-06-01
> **mpnordland said:**
> Great, I'll look at it later, One possible reason may be that I'm right now not passing along the user-agent, the other maybe that I'm not making any difference between content types. I'm going to go over what I have and try to implement it in a better, more comprehensive way. By the way, do you use Code::Blocks too?

Okay, well I'm sure you'll figure that out :)
Yes I'm using Code::Blocks, so I was glad to see you're doing that as well. The linker settings and compiler directories are different for us... I've used static libraries so far.

---

### Post by mpnordland on 2011-06-01
> **sadastronaut said:**
> Is it possible to block access via the local port, so that browsing has to happen via a proxy?
yes, but that is not within the purview of the proxy, but rather of iptables on linux, and IPSEC on windows. On linux, I'm thinking to perhaps set it up as a transparent proxy, but there maybe some other concerns that will make that impossible. 
@roggan87
EDIT: Fixed, I had just the basic version installed, I'm compiling the full version now.

---

### Post by mpnordland on 2011-06-01
Well, Poco is fixed, but in include/Options.h on line 9 it says #include "Iphlpapi.h" The compiler can't find it, and hence I haven't been able to build your code. Where is Iphlpapi.h?

---

### Post by roggan87 on 2011-06-02
> **mpnordland said:**
> Well, Poco is fixed, but in include/Options.h on line 9 it says #include "Iphlpapi.h" The compiler can't find it, and hence I haven't been able to build your code. Where is Iphlpapi.h?

Well sorry about that, it's redundant. I think it might be OS-specific. Since I'm using MinGW I've included "libiphlpapi.a" in the linker settings. So the conclusion is: delete that line. I know there are some files that have to be included instead of windows.h, especially in order to get libpcap working, but they might be included by POCO. Otherwise, look at this example for some guidelines: [http://www.tcpdump.org/sniffex.c]("http://www.tcpdump.org/sniffex.c")

---

### Post by mpnordland on 2011-06-02
Alright, I've learned two things about C++: You have to link to the right libs, and you've got to have the right headers installed. I got it to compile, link and run and this is what I got:

```
No adapter selected: printing the device list:

No interfaces found! Make sure WinPcap is installed.
Segmentation fault

Process returned 139 (0x8B)   execution time : 0.362 s
Press ENTER to continue.
```

I'll be looking further through the code to find the problem. I'm going to add my modified Code::Blocks project as a separate file for linux.

---

### Post by mpnordland on 2011-06-02
Ok, I rearranged the /dev folder in the C++_Rewrite. Both Linux and windows now  have their own directory. In the windows dir should be your original code roggan87, so that should still build on windows, in the linux dir, there should be the small modifications I've made to enable it to at least build on linux. Also, due to some factor I'm not aware of, the linux directory is locked, so some of my mods may not be there.

---

### Post by roggan87 on 2011-06-02
> **mpnordland said:**
> Alright, I've learned two things about C++: You have to link to the right libs, and you've got to have the right headers installed. I got it to compile, link and run and this is what I got:

```
No adapter selected: printing the device list:

No interfaces found! Make sure WinPcap is installed.
Segmentation fault

Process returned 139 (0x8B)   execution time : 0.362 s
Press ENTER to continue.
```

I'll be looking further through the code to find the problem. I'm going to add my modified Code::Blocks project as a separate file for linux.

Alright, but at least you got it to compile! I was also thinking about having separate project files for the different platforms. I think you shouldn't have to point the compiler to all header files for POCO, like I've done, but I could never get it to compile otherwise. Not sure if I've compiled the POCO libs properly, it was a though one to compile on Windows using Code::Blocks.

That's right, you need to have winpcap, or libpcap for linux, installed *and* running in order to get it working. There should be lots of information on that out there, probably at [www.tcpdump.org](www.tcpdump.org). Once we've moved to the proxy instead, we could skip libpcap completely.

---

### Post by roggan87 on 2011-06-02
> **mpnordland said:**
> Ok, I rearranged the /dev folder in the C++_Rewrite. Both Linux and windows now  have their own directory. In the windows dir should be your original code roggan87, so that should still build on windows, in the linux dir, there should be the small modifications I've made to enable it to at least build on linux. Also, due to some factor I'm not aware of, the linux directory is locked, so some of my mods may not be there.

SVN is working terribly slow for me, it takes half a minute just to refresh one directory or enter another. It seems like you've forgotten the subdirectories in both the windows and linux directory.

Maybe this is only meant to be a temporary solution, but I believe we have to think cross-platform all the way. I'll explain. Most of the code will be identical regardless of what platform you'll compile it on. Therefore I think we should try to use the same code, the same project tree etc. The libraries to include will differ though, so the project files would be wise to have different for different platforms. In the code we will encounter stuff that has to be platform-specific, like filepaths, different headers etc. In these cases we can use the preprocessor to include the correct headers, or to define variables. I've tried to implement this at the top of Options.h, it might serve as an example. For bigger functions etc, we'll have to make separate headers and include the correct files in the code, selected by the preprocessor. Hope this makes sense. I'll look at your modifications when I get time.

So long.

---

### Post by mpnordland on 2011-06-02
I was having problems, your right on the cross platform thing, Just revert to revision 80 or so, and you'll be back to the way it was before. I'm thinking about what exactly to do to make it permanently revert.

---

### Post by roggan87 on 2011-06-02
> **mpnordland said:**
> I was having problems, your right on the cross platform thing, Just revert to revision 80 or so, and you'll be back to the way it was before. I'm thinking about what exactly to do to make it permanently revert.

Oh I see. Revision 100 is where I've uploaded the files, before they were split into linux and windows directories.

---

### Post by mpnordland on 2011-06-04
Then there is where you should go. I think we need to setup a process for these decisions, also, we need some clear goals of this rewrite so that we don't just get ourselves going in different directions. We should probably do that first, before continuing development.

---

### Post by roggan87 on 2011-06-05
> **mpnordland said:**
> Then there is where you should go. I think we need to setup a process for these decisions, also, we need some clear goals of this rewrite so that we don't just get ourselves going in different directions. We should probably do that first, before continuing development.

You're totally right about this. It should have been done way back. I've started a document with some directives for development of Net Responsibility. I'll upload it when I'm finished. Any contributions to the document will be welcome :)

---

### Post by roggan87 on 2011-06-06
Alright. I've written some directives to follow. The document can be found here: [https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/C++_Rewrite/dev/DEVELOPERS](https://responsibility.svn.sourceforge.net/svnroot/responsibility/branches/C++_Rewrite/dev/DEVELOPERS)

I don't know how much to include, or how much to exclude, but this is at least a beginning. We can add, edit, change things along the way. If you have suggestions on things to change immediately, please let me know.

I've also restructured the directory layout a bit. Please try to compile using the Linux project file to see if it works as expected.

---

### Post by mpnordland on 2011-06-06
Ok, I'll fill in my parts on the document. Now that this is in place, we can have less surprises. Right now, Every thing looks good. But, we have a BIG problem, The forum isn't quite ready, and I personally do NOT advise going there, for the simple reason that someone has spammed it with porn. I don't know how they did it, but it looks like every thread has it. Note that I did not check all the threads, only two, but I didn't want look any farther. We've got fix that, because we, being an internet accountability software, shouldn't have porn in our forum. Is the website hosted on sourceforge? Also, do I have mod power there? because if I do, I'll get that stuff removed right away. Robert, I'll be emailing this to you as well.

---

### Post by alan_m1 on 2011-06-06
Thanks for share this thread i will look forward to the info and knowledge shared in the post and use & implement the knowledge in future.
This sounds really interesting................
----------------------------
For news group visit [usenet]("http://usenetreviewz.com/") | [supernews]("http://usenetreviewz.com/supernews-review/")

---

### Post by thejambi on 2011-06-07
Hey guys - How do I test running this code? I have been looking around your discussion here and have tried to build it. I think that worked :) but I need help on what I'm looking for to run it.

---

### Post by mpnordland on 2011-06-08
In code::blocks, choose the little green arrow [ATTACH]194554[/ATTACH]

---

### Post by roggan87 on 2011-06-12
> **thejambi said:**
> Hey guys - How do I test running this code? I have been looking around your discussion here and have tried to build it. I think that worked :) but I need help on what I'm looking for to run it.

Well pretty quickly:

[LIST]
[*]Compile the [POCO library]("http://www.pocoproject.org")
[*]Install [libpcap ]("http://www.tcpdump.org")or [winpcap]("http://www.winpcap.org")
[*]Make sure the Net Responsibility source code is linked to the right POCO libs.
[*]Compile Net Responsibility
[*]Run it
[/LIST]

For now it would be easiest to compile it inside Code::Blocks, since the project files are tied to it. When it's time for official release, I *really *think we should look deeper into GNU autotools to get a ./configure make make install solution.

---

### Post by thejambi on 2011-06-18
Alright, well I'm getting the following:

No adapter selected: printing the device list:

No interfaces found! Make sure WinPcap is installed.
Segmentation fault

Process returned 139 (0x8B)   execution time : 0.249 s
Press ENTER to continue.


So I'm guessing I've got libpcap installed wrong. I have no idea. Maybe I just can't do this..

Is there a way I can check if libpcap installed right?

---

### Post by mpnordland on 2011-06-18
Yep, We know about that one, it works on windows, but not on Linux. It'll probably get dropped once the proxy works better. The best way to help this situation would probably be working on the proxy, but you should talk to roggan87 for the definitive answer on that.

---

### Post by thejambi on 2011-06-19
I tried setting this up on my install of Linux Mint 9 (Ubuntu 10.04) instead of Linux Mint 11 (Ubuntu 11.04). I got this:

/home/zach/Projects/NetResponsibility/C++_Rewrite/dev/bin/Debug/net-responsibility-sniffer: 1: Syntax error: "(" unexpected

Press ENTER to continue.

Any idea of where that "(" is?

---

### Post by mpnordland on 2011-06-20
No clue at this moment, try looking in Sniffer.h and Sniffer.cpp

---

### Post by roggan87 on 2011-06-21
> **thejambi said:**
> Alright, well I'm getting the following:

No adapter selected: printing the device list:

No interfaces found! Make sure WinPcap is installed.
Segmentation fault

Process returned 139 (0x8B)   execution time : 0.249 s
Press ENTER to continue.


So I'm guessing I've got libpcap installed wrong. I have no idea. Maybe I just can't do this..

Is there a way I can check if libpcap installed right?

I just realized I've forgotten, you'll have to download the source of libpcap and set up the compiler to find pcap.h. That should of course be set in the project file. There might as well be some windows-specific code that has to be complemented in Sniffer.h and Sniffer.cpp, but it should only be regarding what headers to include. A nice guide to follow on programming with libpcap in linux is found here: [http://www.tcpdump.org/pcap.html](http://www.tcpdump.org/pcap.html)

It is also true as mpnordland is saying, libpcap is the best solution we have at the very moment, but it would be much better if we could complete our own proxy. That would open up the possibilities a lot.

---

### Post by mpnordland on 2011-06-21
Right now, I was waiting for an answer to a question on stackoverflow, but no one seems to know what I need to do. I will just have to forge ahead into the unknown. I looked at that website, maybe I'll take a look and tweak the device choosing code. If anyone has an example of how you use Poco C++'s HTTPSessionFactory please pm me.

---

### Post by roggan87 on 2011-06-21
> **mpnordland said:**
> Right now, I was waiting for an answer to a question on stackoverflow, but no one seems to know what I need to do. I will just have to forge ahead into the unknown. I looked at that website, maybe I'll take a look and tweak the device choosing code. If anyone has an example of how you use Poco C++'s HTTPSessionFactory please pm me.

Sorry I don't know about HTTPSessionFactory. Maybe you can get some help from POCO's forum: [http://pocoproject.org/forum/](http://pocoproject.org/forum/)

---

### Post by mpnordland on 2011-06-22
Yep, that's where I went, I got some info coming in now.

---

### Post by muppett on 2011-06-22
Can I ask why Windows is being supported? Windows already has accountability software. Wouldn't focusing on getting everything working in Linux be priority?

---

### Post by thejambi on 2011-06-22
> **muppett said:**
> Can I ask why Windows is being supported? Windows already has accountability software. Wouldn't focusing on getting everything working in Linux be priority?

I think maybe you just misread the comment about Windows. As far as I know, it is not really supported. 

I am using NetResponsibility in Linux and I'm really liking it. Head to [http://www.netresponsibility.com/](http://www.netresponsibility.com/) to learn more and install!

---

### Post by roggan87 on 2011-06-23
> **muppett said:**
> Can I ask why Windows is being supported? Windows already has accountability software. Wouldn't focusing on getting everything working in Linux be priority?

At the very moment Windows is not supported. To answer your question about getting everything working in Linux, we've taken an active decision to rewrite the whole program in a completely different language, because the one being used up to version 2.0.2 has too many limitations. So instead of spending a lot of time on trying to make Net Responsibility satisfying in Ruby/Python, we'll spend that time on making it the way it should have been done from the beginning. However, we've learned a lot and can reuse much of the previous code, especially the server-side code.

One big problem though is that I'm stuck in Windows for the moment, so I _have to_ develop the new rewrite in a Windows environment. I also think that as we're rewriting the complete software, why limit ourselves to Linux, when we can make it cross-platform? There are other accountability softwares available, but no good open source alternatives. If we make Net Responsibility available for more platforms, the chance of finding more developers also increases.

So the main target is not to port Net Responsibility to Windows, but to rewrite it completely, and in that process include Windows users.

Hope that explains some.
Robert

---

### Post by roggan87 on 2011-06-23
> **thejambi said:**
> Alright, well I'm getting the following:

No adapter selected: printing the device list:

No interfaces found! Make sure WinPcap is installed.
Segmentation fault

Process returned 139 (0x8B)   execution time : 0.249 s
Press ENTER to continue.


So I'm guessing I've got libpcap installed wrong. I have no idea. Maybe I just can't do this..

Is there a way I can check if libpcap installed right?


Alright, I got it working with Linux and LibPcap. The answer was easier than I thought - you have to be root when running the program. I also included some headers in Sniffer.h and installed the package libpcap-dev. However it wasn't catching the input every time. Please try to see what output you get. Once you've chosen input device Net Responsibility should output a 0 for regular URLs and 1 for matches.
I've finally installed Ubuntu again, but will dualboot with Windows as well, so I think this might help in development...

---

### Post by stwilliams on 2011-08-15
Configuring it - I had to type the command grun net-responsibility-config-gui in the terminal, and then I put in my name and password in the username and password window.
I click configure and it says username and password entry wrong 3 times, or something like that and I noticed I had 3 password prompts on Terminal - so I closed it.
I try again, with the correct username and password...
Now, it says..

sudo: no tty present and no askpass program specified

What does this mean, and how do I fix it?

---

### Post by mpnordland on 2011-08-16
Have you tried using the menu item found at Applications>System Tools>Configure Net Responsibility? Otherwise, you can try either 
```

gksudo net-responsibility-config-gui,

```
or
```

sudo net-responsibility-config-cli

```

---

### Post by aerojust on 2011-08-31
Just stumbled upon Net Responsibility. It insalled flawlessly on Ubuntu 11.4 64bit. When I try to configure the account I get

```
/usr/share/net-responsibility/lib/server_connection.rb:63:in `set_config': ERROR (RuntimeError)
Another account have already been set up on your computer, (osbornab). Please delete that account before you use this one.
	from /usr/local/bin/net-responsibility-config-cli:108:in `initialize'
	from /usr/local/bin/net-responsibility-config-cli:119:in `new'
	from /usr/local/bin/net-responsibility-config-cli:119

```

Any Ideas how to fix this. I am 99.9% sure there is no account in existence on this machine. It is a newer install and I am the only one with the root password.

---

### Post by Jordy_224 on 2011-09-06
Hello,

   I'm working on a program that will allow a user to keep his/her own accountability passwords. The password will only be released after the user answers accountability questions. The idea is simple, and similar to an emails password recovery system: ie. 

```
Question 1: What does John 3:16 say?
Answer: 

correct
Your password is ... 
```


I think this is a viable alternative, if the user doesn't have a safe place to keep his/her passwords.

---

### Post by jonathonblake on 2011-09-08
> **Jordy_224 said:**
> 
```
Question 1: What does John 3:16 say?
Answer: 

correct
Your password is ... 
```


One issue I've run into, when using Bible verses, etc as passwords, is that the user knows the material from one translation, but the program, etc expects the verse from a different translation.

The second issue I've run into, is exemplified by Malachi 3:24. Whilst it is fairly easy to figure out what that verse is, in other places, such as Psalm 59:1, it is extremely unobvious: "For the director. Do not destroy. A miktam of David, when Saul sent people to watch his house and kill him", or "For the End: For things yet to be changed for a pillar inscription;by David; for teaching.", or "Deliver me from my enemies of God; Protect me from those who rise against me".

If the instructions include the specific hardcopy, or etext that is used, then using the Bible verses will probably work. If it is a generic, "use the KJV", it won't work.

jonathon

---

### Post by mpnordland on 2011-09-09
First @Jordy_224, what is the purpose of this? It seems to resemble a password manager.

Second @aerojust, Please add a topic to the Net Responsibilty Forum. It is located at [http://www.netresponsibility.com/forum/](http://www.netresponsibility.com/forum/) . You can sign in with your net responsibility password.

---

### Post by roggan87 on 2011-10-16
[SIZE="4"][COLOR="Red"]NOTE! This is not the place to discuss Net Responsibility any more![/COLOR][/SIZE]

The best place is the [forum at our website]("http://www.netresponsibility.com/forum/"). Simply use your Net Responsibility account when you log in.

If you want to contact us in private, or having problems logging in using your account, you can use the [contact form]("http://www.netresponsibility.com/contact.php").

Thanks,
Robert

---

### Post by mpnordland on 2011-10-16
You can still post something here, but We'll be paying more attention to our new forums. See you all at [http://www.netresponsibility.com/forum/](http://www.netresponsibility.com/forum/) !

---

### Post by Mickeyj4j on 2011-11-03
hi I have had net responsibility installed for a long time in Linux Mint 9 which is based on ubuntu 10.04 LTS (long term support). for a ling time it has not been sending reports to the emails. i then added my own address to check and nothing is sent. This is supposed to be an automatic process. done every 2-4 weeks is it not. 

what am i missing or what has changed in my os to make it stop workling. 

i recently got the email staring

 "A serious problem that may affect your Net Responsibility installation have been encountered. In some Linux distributions the latest dsniff package seems to be broken. That means Net Responsibility will exit with the following message:
 
net-responsibility-daemon[3121]: Starting
net-responsibility-daemon[3121]: Caught interrupt. Exiting.
Please try to open a terminal and enter this command: "sudo net-responsibility-daemon --nodaemon" to see if you get the error message stated above."

running the comand does not give any errors so i know its not that. 

what can i try to fix this problem. maybe its another app or process that i have installed that could be either conflicting with it or it has been turned off somehow.

---

### Post by mpnordland on 2011-11-04
Does sending a test mail work? Open the configuration utility and click test mail, or run 
```

sudo net-responsibility-report --testmail

```
in terminal

---

