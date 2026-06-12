---
title: "Ubuntu one refuses to work"
date: 2009-10-14
forum: Ubuntu One (CLOSED)
---

### Post by Sashin on 2009-10-14
Anyone else notice this? When I click on ubuntu one once, nothing happens. Twice I get an ! in the panel and an error box. Also when I go to the ubuntu one folder and hit connect nothing happens.

Is this specific to only me, or is this a widespread problem?

---

### Post by tuxxy on 2009-10-14
The Ubuntu one bug got fixed with the latest Karmic updates 1.0.1.   Make sure you have run all updates and try again.

---

### Post by Sashin on 2009-10-14
I have updated and I'm even on the main server

---

### Post by autocrosser on 2009-10-14
It was not working for me, so I rebooted & then all worked...

---

### Post by Sashin on 2009-10-14
I rebooted several times, doesn't work.

---

### Post by hanzomon4 on 2009-10-14
It's working for me... even tomboy syncs

---

### Post by mocoloco on 2009-10-14
Won't work for me either. Get the ! in the panel, and when it pulls up the link to the site and I try to sign in it just reloads the sign in page again.

---

### Post by Sashin on 2009-10-15
Come to think of it I never added my computer, it never asked me to and I can't find an option to either from the desktop or the web interface.

---

### Post by Sashin on 2009-10-15
I get how it works now, but I'm screwed as it can't be fixed. After trying it out on some other computers I've found that the first time you start ubuntu one it offers to connect your computer to your account. If you are using a non firefox browser as default or close that window, it will never return and there is no possible way to use ubuntu one. 

That's what I'm getting based on a few computers.

---

### Post by Sashin on 2009-10-15
This is a serious problem, it really needs to be addressed. If a user closes the window that pops up on first launch they are barred from ubuntu one (tested on 3 computers). Even uninstalling it and reinstalling it doesn't work, and the configuration files aren't in ~.

This is what happens when I try from terminal.

```
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/status: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/status: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

```

---

### Post by Sashin on 2009-10-15
If I open it a second time, while the other one is running a cloud with an ! comes in the panel and the ubuntu one preferences window comes up. I can't connect and if I go to the web I don't get an option to add this computer. 

This comes up in terminal.

```
Ubuntu One client applet already running, quitting
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/config: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
DBusException(dbus.String(u'Message did not receive a reply (timeout by message bus)'),)
DBusException(dbus.String(u'Message did not receive a reply (timeout by message bus)'),)

```

---

### Post by ndefontenay on 2009-10-15
I'm having problem with ubuntu one as well.

I managed to add my computer to my account. I've uploaded a file there but it's not synchronizing with my lapy.

I think you should post your bug to launchpad.net.

Nico

---

### Post by Sashin on 2009-10-15
I already have. But I didn't include all the terminal stuff and detailed description.

---

### Post by joshuahoover on 2009-10-15
My apologies for all the trouble folks are having with the service right now. We're experiencing some issues on the server side that are causing problems with authorizing the computer and authenticating. We're on it and trying to get this fixed ASAP. 

Thank you,

Joshua

---

### Post by Sashin on 2009-10-15
Wait so you're saying those errors are from the server side?

---

### Post by andrea000 on 2009-10-15
I'm seeing that now as well worked for about
3 hours trying to get going with no luck.I'LL
wait till you get it going again.

---

### Post by adamis on 2009-10-20
Are there still server issues going on with UbuntuOne? I'm having a lot of these same issues and I haven't been able to figure out what is going on. Last night I was able to get UbuntuOne to upload about 2gb worth of document files but today it hasn't uploaded a single file and it's had hours of internet connection time to do it.

Clicking once on the applet icon brings up a message that all of my files are up to date but in reality there is still 12gb worth of data that needs to be uploaded.

---

### Post by joshuahoover on 2009-10-22
> **adamis said:**
> Are there still server issues going on with UbuntuOne? I'm having a lot of these same issues and I haven't been able to figure out what is going on. Last night I was able to get UbuntuOne to upload about 2gb worth of document files but today it hasn't uploaded a single file and it's had hours of internet connection time to do it.

Clicking once on the applet icon brings up a message that all of my files are up to date but in reality there is still 12gb worth of data that needs to be uploaded.

We've been doing some fairly big infrastructure updates lately and this should address many, if not all of the problems you and others have been experiencing. I apologize for the inconvenience this has caused you and thank you and all the others using Ubuntu One for their patience as we tune the service.

Thank you,

Joshua

---

### Post by crimsdings on 2009-10-22
So this is a know problem ? cause i can't login anymore

```
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/status: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/status: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1

```

any eta ?

---

### Post by Hakkatuka on 2009-10-22
Deleting everything in ~/.local/share/ubuntuone/syncdaemon/ directory fixed it for me. It gets recreated as soon as you start ubuntuone client again. Also make sure you have the computer added just once on one.ubuntu.com website.

---

### Post by chris.willis on 2009-10-30
I have similar issues. I added my machine and it wouldn't work. I tried a number of threads and suggestions. one was to delete and re-add the machine but after deleting, there's no option to add. It's a shame because Ubuntu One was one of the bigger selling points for Karmic. I think it'll be much easier to delete Ubuntu One instead of spending more hours on it.

---

### Post by beefjerkymonster on 2009-10-31
It doesn't work for me either.

Fresh install of 9.10 yesterday, 64 bit. I just tried ubuntu one today, and I never got a window to add a computer when I first ran the program. I've tried a few things (looked ALL over the ubuntu one site, and deleted/re-installed the program). The ubuntu one site shows that I don't have any computers added (obviously). In my notification area it shows a cloud with a !.

I will not re-install Ubuntu to make it work.

---

### Post by Sennaista on 2009-10-31
> **beefjerkymonster said:**
> It doesn't work for me either.

Fresh install of 9.10 yesterday, 64 bit. I just tried ubuntu one today, and I never got a window to add a computer when I first ran the program. I've tried a few things (looked ALL over the ubuntu one site, and deleted/re-installed the program). The ubuntu one site shows that I don't have any computers added (obviously). In my notification area it shows a cloud with a !.

I will not re-install Ubuntu to make it work.

Yup, I have the exact same issue with 64 bit Karmic.

---

### Post by Sennaista on 2009-10-31
I managed to solve my problem.

Open Synaptic and make sure you have ubuntuone-client-tools is installed, if not then install it. Then open a terminal and run this command:

```
u1sync --authorize

```

It will take a few seconds, an "authorized" massage is printed in the terminal and at this point Firefox should open and load a page that would allow you to add your computer to your U1 subscription. After doing so you can test it by copying a file into your U1 folder and see if it's uploaded to your personal space or not. You might have to right-click on the U1 icon in the notification area and click on "connect" for the upload to begin.

Hope this helps.

---

### Post by Sennaista on 2009-10-31
Spoke too soon. After a restart I still have the same problem, U1 client won't connect.

---

### Post by Sennaista on 2009-10-31
There's work around that seems to work. I found it in a bug report on Launchpad:

Exit U1 client.

Run: ```
rm -rf ~/.config/ubuntuone
```Restart U1 client.

Now I can connect whenever I want to but the synching can be a bit hit and miss. Sometimes files do get uploaded and sometimes not. I guess it will take a while for all the bugs to be ironed out.

---

### Post by x-na on 2009-10-31
> **Sennaista said:**
> ```
u1sync --authorize

```


I'm with the same problem, I never got the webpage I could add my machine. Running that above command only ouputs this:

ERROR:dbus.proxies:Introspect error on org.freedesktop.NetworkManager:/org/freedesktop/NetworkManager: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files

And does not do anything. Also running 64-bit Karmic. Installed all the updates etc.

And yes, I removed network-manager (more like -damager) because it doesn't work well with static IPs (never has, in my POV). But yes, Ubuntu One seems to have too much problems, easier to just remove it than to fight to get it working.

---

### Post by arnab_das on 2009-11-01
same problem here. :(

ubuntu one simply wont connect to the ubuntuone server.

---

### Post by x-na on 2009-11-01
> **x-na said:**
> I'm with the same problem, I never got the webpage I could add my machine.

Installing network-manager, rebooting and then running Ubuntu One did the trick. After that it gave me the option to add my machine. After adding my machine I was able to remove network-manager and still use Ubuntu One.

---

### Post by catraeth on 2009-11-01
Hi - my issue is slightly different - I can log in to Ubuntu One and see my files, but when I click on one to open it, after a couple of minutes I get a 'server timed out message'.  These are just a couple of test files, but if we're going to use One we need to be able to trust that our data is safe and accessible...

---

### Post by niw_uk1964 on 2009-11-01
I've given up on it, both of my machines can't connect to the service once past the initial stage of adding them to the account. I've uninstalled it as I have better things to do chase my tail chasing buggy software.

---

### Post by m4lte on 2009-11-01
**I don't get a website** to connect my computer to my account.

I tried
*rm -rf ~/.config/ubuntuone*
and
*u1sync --authorize*
without any success.

I'm running 9.10 and I use WICD, *not* network-manager.
Any help?

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
i cant upload files it just freezes

---

### Post by adamis on 2009-11-01
I've noticed that on a laptop any time U1 get's interrupted by sleeping or standby that it doesn't seem to ever recover. In general it seems like the sync daemon can't recover if it is ever interrupted like it just thinks that all of the files are there and it doesn't ever attempt to sync up again.

I can't give up hope on it yet as the service is something I need and I do like being able to support Ubuntu in some way but it's got to be better then this. I paid the $10 monthly fee for the extra storage and I think at this rate if these problems aren't resolved by the end of November I'm going to cancel my subscription. When most of the issues are resolved then I would consider resubscribing.

---

### Post by joshuahoover on 2009-11-02
> **adamis said:**
> I've noticed that on a laptop any time U1 get's interrupted by sleeping or standby that it doesn't seem to ever recover. In general it seems like the sync daemon can't recover if it is ever interrupted like it just thinks that all of the files are there and it doesn't ever attempt to sync up again.

I can't give up hope on it yet as the service is something I need and I do like being able to support Ubuntu in some way but it's got to be better then this. I paid the $10 monthly fee for the extra storage and I think at this rate if these problems aren't resolved by the end of November I'm going to cancel my subscription. When most of the issues are resolved then I would consider resubscribing.

Sorry for the troubles with Ubuntu One when coming out of sleep/hibernate. This is a known issue that we need to fix. [https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/457147](https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/457147)

Thank you,

Joshua

---

### Post by marquinos on 2009-11-04
> **Hakkatuka said:**
> Deleting everything in ~/.local/share/ubuntuone/syncdaemon/ directory fixed it for me. It gets recreated as soon as you start ubuntuone client again. Also make sure you have the computer added just once on one.ubuntu.com website.

This works for me! Thanks Hakkatuka! :D

---

### Post by beacon on 2009-11-05
I tried to use Hakkatku's suggestion, but after typing in the command, I am told  'command not found'.

---

### Post by md81544 on 2009-11-05
> **beacon said:**
> I tried to use Hakkatku's suggestion, but after typing in the command, I am told  'command not found'.

The first two letters that you typed are "r" then "m", right?

---

### Post by beacon on 2009-11-05
No. I may show my ignorance, but I simply used sudo followed by cutting and pasting the command.

---

### Post by faical117 on 2009-11-06
doesn't work for me too :mad:

---

### Post by jondecker76 on 2009-11-07
Deleting ~/.local/ubuntuone/syncdaemon contents and restarting the UbuntuOne client also worked for me. This is the first things have worked for me since installing 9.10... (I finally have a cloud icon in my taskbar without a "!" in it!)

My tomboy notes didn't sync though - anyone else with this problem?

---

### Post by Roger Allott on 2009-11-10
Update Manager sent me through updates for three UbuntuOne packages last night, but my problems persist as regards connecting via Nautilus in 9.04.

This problem should be rather embarrassing for Canonical, IMHO, because AFAIK it is one of the first services that they've tried to sell to the mass public.

It's one thing to have bugs and gremlins in software given away free of charge, but something else entirely when it is sold. I would hope to see some sort of recompense offered to those people who have shelled out the £10 per month for the 50Gb service (or rather, non-service).

I'd like to ask the UbuntuOne team to do themselves, and us, a favour. When you are completely confident that all the bugs thus far identified in UbuntuOne have been solved, please send a mass PM to everyone who has posted in this sub-forum to let us know that the service is now working, including where necessary any instructions we need to carry out to clean up any residual problems.

Could someone please confirm that this will happen?

---

### Post by beacon on 2009-11-12
I would second the motion of Roger Allott and would hope that we might be provided with the state-of-play. I had too many problems with Koala and went back to Jaunty. Now I am trying to install UbuntuOne, which on the surface seems quite simple. Unfortunately, the reality is different. I have updated and added the PPA, but when I go go the next step (install ubuntu-client-gnome) I get the message: 'Firefox does not know to open this address, because the protocol (apt) isn't associated with any program'. If I follow the alternative direction and go to synaptic, I find there is no ubuntu program at all. 

A number of problems have been reported. It would help a good deal if we could know if they are unresolved bugs in the program, or whether we the users are doing something wrong.

---

### Post by gerowen on 2009-11-18
Ubuntuone worked great for me until I installed wicd and removed the Gnome Network Manager, because somewhere between 9.04 and 9.10 the Gnome Network Manager got completely fooked and disconnects from my network once every 10 minutes or so for no reason, and sometimes refuses to reconnect, and I'm sitting about 10 feet from my wireless router.  Apparently it's dependent on the Gnome Network Manager though and not just internet connectivity in general, so if you have to use wicd or something like it to use internet, you're forced into not being able to use the Ubuntuone app.

---

### Post by Fraoch on 2009-11-18
UbuntuOne was also not working for me, 64-bit Karmic.  I missed the authorization page on first start because I'm also not using Firefox as the default browser.

I tried:

```
u1sync --authorize
```

but needed to install ubuntuone-client-tools first, which for some reason was not installed while all the other ubuntuone software was.

That worked, I was able to add my machine and have it appear on the Ubuntu One web page.

What's not working, and I haven't seen this mentioned in this thread, is Nautilus integration.  I have the Ubuntu One folder, but when I click the "Connect" icon nothing happens.  No data is transferred to or from Nautilus to Ubuntu One and Nautilus does not see the test files I placed on Ubuntu One using the web interface.

I would rather not rely on the web interface, it's very slow.  Changes take a minute or two to be visible, I'm never sure if I added something successfully or not.  I have to view the other tabs and go back to the "Files" tab to see the changes.

Oh I have network-manager installed, so that should not be the problem.  It's like the synch daemon is not running, but System Monitor - Processes shows that it is (sleeping at the moment).

I guess I'll wait until more bugs get worked out.:(

---

### Post by Fraoch on 2009-11-19
Hmm, improvement today!  I had to reboot tonight due to a crash of another (unrelated) program, and today everything seems to be working except the icon/notification which is supposed to tell me my computer is synching with Ubuntu One.

I had set the client software to use the notification icon.

Also today I can't access the client software GUI from Applications - Internet - Ubuntu One.  It asks for access to the keyring then does nothing.

At least I am synching today.

---

### Post by josephpmh on 2009-11-21
This worked for me, altho' my command was 

rm ~/.local/share/ubuntuone/syncdaemon  (note the extra folder layer "share").  Then a restart, and sharing began.

Thanx Jon.

> **jondecker76 said:**
> Deleting ~/.local/ubuntuone/syncdaemon contents and restarting the UbuntuOne client also worked for me. This is the first things have worked for me since installing 9.10... (I finally have a cloud icon in my taskbar without a "!" in it!)

My tomboy notes didn't sync though - anyone else with this problem?

---

### Post by gerowen on 2009-11-21
Wow, deleting that folder as well as my $HOME/.config/ubuntuone/ubuntuone-client.conf file actually makes it connect even if I'm using wicd.

---

### Post by pizza-is-good on 2009-11-21
> **mocoloco said:**
> Won't work for me either. Get the ! in the panel, and when it pulls up the link to the site and I try to sign in it just reloads the sign in page again.
Same here!

> **joshuahoover said:**
> My apologies for all the trouble folks are having with the service right now. We're experiencing some issues on the server side that are causing problems with authorizing the computer and authenticating. We're on it and trying to get this fixed ASAP. 

Thank you,

Joshua

I've been having this problem for weeks...... Not fixed as of today yet.

---

### Post by joshuahoover on 2009-11-24
> **marcusdean.adams said:**
> Ubuntuone worked great for me until I installed wicd and removed the Gnome Network Manager, because somewhere between 9.04 and 9.10 the Gnome Network Manager got completely fooked and disconnects from my network once every 10 minutes or so for no reason, and sometimes refuses to reconnect, and I'm sitting about 10 feet from my wireless router.  Apparently it's dependent on the Gnome Network Manager though and not just internet connectivity in general, so if you have to use wicd or something like it to use internet, you're forced into not being able to use the Ubuntuone app.

Please try our latest release in our beta PPA. Installation instructions for those on Karmic can be found here: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/836](https://answers.edge.launchpad.net/ubuntuone-client/+faq/836)

---

### Post by gerowen on 2009-11-24
> **joshuahoover said:**
> Please try our latest release in our beta PPA. Installation instructions for those on Karmic can be found here: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/836](https://answers.edge.launchpad.net/ubuntuone-client/+faq/836)

The latest version of Network-Manager?  My Ubuntu One started working recently (See previous post, about 2 or 3 back), but I will check out the betas of Network Manager, thanks!

---

### Post by smdeep on 2009-11-25
> **Hakkatuka said:**
> Deleting everything in ~/.local/share/ubuntuone/syncdaemon/ directory fixed it for me. It gets recreated as soon as you start ubuntuone client again. Also make sure you have the computer added just once on one.ubuntu.com website.

I installed on Jaunty and it would not login at all as my default browser was Chrome. So I followed the tip above and changed the default browser to Firefox and it works like a charm.

Thanks for the tip.

---

### Post by joshuahoover on 2009-11-25
> **smdeep said:**
> I installed on Jaunty and it would not login at all as my default browser was Chrome. So I followed the tip above and changed the default browser to Firefox and it works like a charm.

Thanks for the tip.

Good to hear it's working for you! Just to let others know, I've tested Ubuntu One with Chromium and was able to setup Ubuntu One using Chromium as my default browser.

---

### Post by shane2peru on 2009-11-27
So is WICD a problem with this?  I really like WICD, and really don't want to mess around with the Network-Manager.

Shane

---

### Post by philinux on 2009-11-28
WICD is indeed the problem. Karmic default install but I installed wicd. Ubuntuone does not connect.

Reverting to network-manager and deleting the synch daemon folder works.

---

### Post by joshuahoover on 2009-11-30
> **shane2peru said:**
> So is WICD a problem with this?  I really like WICD, and really don't want to mess around with the Network-Manager.

Shane

Hi Shane,

The solution is to use our beta PPA instead of the Karmic packages. Instructions on how to do this are here: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/836](https://answers.edge.launchpad.net/ubuntuone-client/+faq/836)

Thank you,

Joshua

---

### Post by shane2peru on 2009-11-30
> **joshuahoover said:**
> Hi Shane,

The solution is to use our beta PPA instead of the Karmic packages. Instructions on how to do this are here: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/836](https://answers.edge.launchpad.net/ubuntuone-client/+faq/836)

Thank you,

Joshua

Well I took the time to figure out how to configure network-manager to work with static IP address.  I like network-manager even less after figuring it out, it is just not up to par.  Just switched back to wicd, and installed the PPA UbuntuOne client, seems to be working thus far.  Thanks!

Shane

---

### Post by Irritated on 2009-12-08
I've never got Ubuntu One to work on my Desktop computer (Works fine on my laptop). As far as I ever got was clicking Application> Internet> Ubuntu One. It just stalls for a few minutes before giving me errors like 
"Ubuntu One:Error. 
Authorization Error [Errno socket error][Errno 104] Connection reset by peer" 
or " Ubuntu One:Error
Authorization Error
[Errno socket error][Errno 110] Connection timed out"
I am connected to the internet through a proxy and I have set the http_proxy variable and the internet in general works fine. Also Dropbox won't work either.

---

### Post by joshuahoover on 2009-12-15
> **Irritated said:**
> I've never got Ubuntu One to work on my Desktop computer (Works fine on my laptop). As far as I ever got was clicking Application> Internet> Ubuntu One. It just stalls for a few minutes before giving me errors like 
"Ubuntu One:Error. 
Authorization Error [Errno socket error][Errno 104] Connection reset by peer" 
or " Ubuntu One:Error
Authorization Error
[Errno socket error][Errno 110] Connection timed out"
I am connected to the internet through a proxy and I have set the http_proxy variable and the internet in general works fine. Also Dropbox won't work either.

Unfortunately, Ubuntu One does not work behind a proxy right now.

---

### Post by Pifilatakanemu on 2010-02-22
I'm using 9.10 with the latest U1 out of the beta-PPA. 

U1 claims to have updated all files, although it's obvious that this ain't right. the files on the server were updatet 4 months ago when the connection worked last time.

I have my laptop connected twice but I can not delete it:


[https://bugs.launchpad.net/ubuntuone-servers/+bug/524193](https://bugs.launchpad.net/ubuntuone-servers/+bug/524193)


how to solve this issue??

---

### Post by tommynz1975 on 2010-03-09
> **joshuahoover said:**
> Unfortunately, Ubuntu One does not work behind a proxy right now.


This could be the problem, as my provider xtra use a proxy. They can by pass the proxy if the user can prove its the proxy upsetting things.

---

