---
title: "[SOLVED] Requesting help troubleshooting a firestarter error"
date: 2006-04-21
forum: Server Platforms
---

### Post by bswilson on 2006-04-21
Friends,

I am requesting some help troubleshooting an error that I see when I start my Ubuntu 5.10 system (2.6.12-10-386).

When I start up my computer, everything seems to be fine.  But once I log into Gnome (my runlevel is a normal 5), I see this error message:

[IMG]http://img47.imageshack.us/img47/2859/firestartererrormessage5pr.png[/IMG]

There does not seem to be any problem with my iptables firewall rulebase; I mean, it works just fine based on my testing and use.

I of course have gone into /var/log/ to try to find some reason for this message, but I can't find anything useful.  Can someone point me in the right direction?

---

### Post by mjm115 on 2006-04-21
> **bswilson]Friends,

I am requesting some help troubleshooting an error that I see when I start my Ubuntu 5.10 system (2.6.12-10-386).

When I start up my computer, everything seems to be fine.  But once I log into Gnome (my runlevel is a normal 5), I see this error message:

There does not seem to be any problem with my iptables firewall rulebase said:**
> 

In order for a regular user to be able to launch Firestarter, the user must be given additional privileges. **sudo gedit /etc/sudoers** and add the following line at the end: 

[QUOTE]username ALL= NOPASSWD: /usr/bin/firestarter 

you can find more information for Firestarter at [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by bswilson on 2006-04-21
You know what?  I left out an important piece of information.

When firestarter launches, I get prompted for the root password by a *[I]_gksudo_*[/I] dialog box -- that error I posted in my original entry shows **after** I enter my password (and yes, it's the right password).

Does that make any difference?

---

### Post by mjm115 on 2006-04-21
[QUOTE=bswilson]You know what?  I left out an important piece of information.

When firestarter launches, I get prompted for the root password by a *[I]_gksudo_*[/I] dialog box -- that error I posted in my original entry shows **after** I enter my password (and yes, it's the right password).

Does that make any difference?[/QUOTE]

What happens if you do it from a terminal screen?

sudo /usr/sbin/firestarter

---

### Post by RavenOfOdin on 2006-04-21
I've only seen that sort of error if a problem in /etc/group boots you out of the admin or adm sections.

Check there and see if you're under those lines.

---

### Post by bswilson on 2006-04-24
```
$ sudo /usr/sbin/firestarter
Password:
Firewall started
```

When I run firestarter from the CLI, it works just fine (e.g. the expected way).  Of course, the terminal session is tied to the GUI application when I don't add the trailing ampersand.

I checked also in /etc/group for my userid in the admin and adm groups; that was set up properly too.

Is there no additional log file that I might check?  I would guess that iptables/netfilter logs to /var/log/messages or /var/log/syslog, but I can't determine where the firestarter application sends its log data...

---

### Post by bswilson on 2006-05-18
[SIZE="4"]Update[/SIZE]

Well, friends, I still have this problem.  My **/etc/sudoers** and **/etc/groups** files are properly configured per the great advice in this thread.

As I indicated above, running firestarter from the command line works just fine too, with no errors.  When I launch the firestarter GUI from Gnome, that works well too.

My only problem is the whacky error message (see first post in thread) that I get when I start Gnome for the first time.

Can **anyone else** provide any help?

---

### Post by meshback on 2006-05-21
[QUOTE=bswilson]
Can **anyone else** provide any help?[/QUOTE]

There's another thread on this same problem.  I managed to fix mine by removing the extra spaces after the command.  If you go to System > Preferences > Sessions.  Click on Startup Programs, highlight the firestarter command and click Edit.  If there are any spaces after the word firestarter, delete those and click OK.

Give that a shot.

---

### Post by bswilson on 2006-05-22
Thanks very much!  This did solve my problem.  I'm surprised that this hasn't been documented somewhere as a known issue or defect.

For the benefit of everyone else, here is a screen shot of the blank spaces you need to remove.

---

