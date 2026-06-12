---
title: "Cannot browse web when DansGuardian enabled!"
date: 2007-04-13
forum: Ubuntu Christian Edition
---

### Post by xilix on 2007-04-13
Hello,
on my Ubuntu CE v2.2 I can only browse the web with Firefox 2.0.0.3 or Opera when DansGuardian is disabled.

The Firefox-error when DansGuardian is enabled: The proxy server is refusing connections

I tried to lock or to unlock Firefox Proxy in DansGuardian, and I restartet Firefox and I also tried to restart Ubuntu. But it doesn't work.

Does anyone know what to do?

Greetings, xilix

---

### Post by accludetuner on 2007-04-15
It sounds like the proxy settings in your web browsers are not configured correctly.  

Make sure dansguardian is enabled.  Select "Unlock firefox proxy".  
In firefox, go to Edit > Preferences > Network > Connection Settings.  Select "Auto detect proxy settings" and try it again.  If it works, go back to dansguardian and lock the firefox proxy.  Let us know if that took care of it or not.

---

### Post by xilix on 2007-04-16
It didn't work. After selecting "Autodetect Proxy Settings for this network" (and with or without Firefox-restart) the selection was "Direct connection to the internet", but I couldn't open a website...

But I agree with you that something with my proxy-settings must be wrong...

xilix

---

### Post by aaronmc on 2007-04-20
Stop looking at porn

---

### Post by duns0014 on 2007-04-22
I'd suggest disabling DansGuardian, I think you're ready for the internet.

---

### Post by mhancoc7 on 2007-04-22
> **aaronmc said:**
> Stop looking at porn

> **duns0014 said:**
> I'd suggest disabling DansGuardian, I think you're ready for the internet.

Let's try to be helpful. Please!

Jereme

---

### Post by mysticrider92 on 2007-04-23
Are you going through a proxy or firewall? You might need to set that up to allow connections through it. I personally don't have much experience with these, but someone else might be able to help.

[edit] With the firewall and proxy I was asking about, I meant connecting to the internet through another box or something with that built in. Just wanted to clear that up.

---

### Post by dakotadare2b on 2007-04-23
> **xilix said:**
> Hello,
on my Ubuntu CE v2.2 I can only browse the web with Firefox 2.0.0.3 or Opera when DansGuardian is disabled.

The Firefox-error when DansGuardian is enabled: The proxy server is refusing connections

I tried to lock or to unlock Firefox Proxy in DansGuardian, and I restartet Firefox and I also tried to restart Ubuntu. But it doesn't work.

Does anyone know what to do?

Greetings, xilix

I had problems like you describe when I had another firewall (Firestarter) running in conjunction with the CE setup of Dansguardian/Firehol. Once I removed Firestarter, I was good. So make sure you don't have any other firewalls running, which may cause conflicts.

God Bless,
Randy

---

### Post by xilix on 2007-04-27
> **dakotadare2b said:**
> I had problems like you describe when I had another firewall (Firestarter) running in conjunction with the CE setup of Dansguardian/Firehol. Once I removed Firestarter, I was good. So make sure you don't have any other firewalls running, which may cause conflicts.

God Bless,
Randy

No, I didn't install Firestarter or any other firewall. I just was running the 'convert-me'-script a few times (because I had some issues with e-Sword) and after that I have this problem.

Probably I will make a fresh install of Ubuntu CE v3.0 and everything is OK...

xilix

---

### Post by dsp.wang on 2007-04-28
> **xilix said:**
> It didn't work. After selecting "Autodetect Proxy Settings for this network" (and with or without Firefox-restart) the selection was "Direct connection to the internet", but I couldn't open a website...

But I agree with you that something with my proxy-settings must be wrong...

xilix

@xillix 

1) enable DansGuardian, set filtering level, unlock Firefox proxy, then click "save & exit"
2) open Firefox, Edit->Preferences->Advanced->Network->Connection->Settings, select Auto-detect proxy settings.  Exit and restart Firefox.  Go to any URL.
3) open DansGuardian, lock Firefox proxy, then click "save & exit".

That's how I did it when I had the same problem.

---

### Post by xilix on 2007-04-29
> **dsp.wang said:**
> @xillix 

1) enable DansGuardian, set filtering level, unlock Firefox proxy, then click "save & exit"
2) open Firefox, Edit->Preferences->Advanced->Network->Connection->Settings, select Auto-detect proxy settings.  Exit and restart Firefox.  Go to any URL.
3) open DansGuardian, lock Firefox proxy, then click "save & exit".

That's how I did it when I had the same problem.

Same problem as in my former post. Probably he can not detect the right network automatically. But thats OK, I will make a fresh installation of v3.0 (looking forward to it :)  ) and the problem will be solved...

thank you all
xilix

---

### Post by bricin on 2007-05-01
I am also struggling with this issue (and before anyone suggests being ready for the internet let me suggest that while I might be, my kids aren't:-).

I have tried the directions listed here but when locking the Firefox settings it always reverts back to Direct Connect which appears to bypass Dansguardian.

Any thoughts? When enabled & locked firefox.cfg has
//
lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", "8080");
lockPref("network.proxy.type" ,"1");
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1");

This results in "The proxy server is refusing connections..."

Also none of the other network tools I can find will work, e.g. Add/Remove, ping.

Thanks for any and all help on this.

---

### Post by accludetuner on 2007-05-02
your .cfg file looks right.

Can you get any internet connection with dansguardian disabled?  You should be able to ping & traceroute a site or IP without it enabled.  It sounds like you have a connection issue not related to dansguardian.


xilix -  did you ever resolve your issue?

---

### Post by bricin on 2007-05-02
accludetuner,

With dansguardian disabled the connection works fine so this isn't a generalized connection issue, it only occurs when enabled.

Any other settings I should look into?

---

### Post by Cigar Jack on 2007-05-02
I'm having the same issues. The only thing I can think of is that my ethernet is on eth2 not eth0 but I don't seen a configuration for that anywhere.

---

### Post by Cigar Jack on 2007-05-02
I've got a ton of junk on my system (not CE stuff)  I'm going to do a wipe and reinstall with plain fiesty and just install DG.

---

### Post by ceti on 2007-05-05
> **bricin said:**
> I am also struggling with this issue (and before anyone suggests being ready for the internet let me suggest that while I might be, my kids aren't:-).

I have tried the directions listed here but when locking the Firefox settings it always reverts back to Direct Connect which appears to bypass Dansguardian.

Any thoughts? When enabled & locked firefox.cfg has
//
lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", "8080");
lockPref("network.proxy.type" ,"1");
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1");

This results in "The proxy server is refusing connections..."

Also none of the other network tools I can find will work, e.g. Add/Remove, ping.

Thanks for any and all help on this.


Actually, make sure your **firefox.cfg** file looks like this:

[B] //
unlockPref("network.proxy.http", "127.0.0.1");
unlockPref("network.proxy.http_port", "8080");
unlockPref("network.proxy.type" ,"1");
unlockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1");

[/B]Now, you can go to Firefox > Edit > Preferences > Advanced > ..... and check **direct connection**.
Hope this helps.

Cheers

---

### Post by bricin on 2007-05-05
If I set this to Direct Connection then it bypasses DansGuardian.

The problem is not that I can't get an internet connection. The problem is that with DansGuardian enabled and Firefox set to point to the local proxy *nothing* works. I can either disable DansGuardian or reset the proxy settings. But that isn't a solution since I installed this to block *some* sites.

Any other settings I should be looking at?

---

### Post by mhancoc7 on 2007-05-05
> **bricin said:**
> If I set this to Direct Connection then it bypasses DansGuardian.

The problem is not that I can't get an internet connection. The problem is that with DansGuardian enabled and Firefox set to point to the local proxy *nothing* works. I can either disable DansGuardian or reset the proxy settings. But that isn't a solution since I installed this to block *some* sites.

Any other settings I should be looking at?

Are you using the dansguardian GUI to enable/disable the filtering? Are you running Edgy or feisty? If you are running feisty I would suggest that you use the new dansguardian install script and then use the GUI to edit the filter settings.

Jereme

---

### Post by bricin on 2007-05-07
Jereme,

I am using the GUI to enable/disable filtering. I am running Feisty.

What is the new install script? I used the latest I could find (tagged as Feisty) from your CE site. Is there something better?

Thanks for the help and thanks for pulling this together in the first place.

---

### Post by mhancoc7 on 2007-05-07
> **bricin said:**
> Jereme,

I am using the GUI to enable/disable filtering. I am running Feisty.

What is the new install script? I used the latest I could find (tagged as Feisty) from your CE site. Is there something better?

Thanks for the help and thanks for pulling this together in the first place.

Hmm.

Sounds like you are already using the latest script. I am not sure what is going on then.

I will take another look at the script to see if I spot any issues.

Thanks, Jereme

---

### Post by Vin_L on 2007-05-09
I cannot get the connection settings to stay on auto detect proxy settings either. The difference with mine is that I can browse but Dansgardian is bypassed because Firefox is set to direct connect. I tried all the advice in this thread to no avail. The next thing I will try is to unload any extensions I have loaded in Firefox to see if that makes a difference.
Other than this little glitch I am loving Ubuntu (I tried it at version 5.04 and am re-visiting it now quite a difference in that short time). I am especially impressed with the CE.  I do want to have an internet filter running though before I commit to using this full time including family.
I'll report back if I have any luck.

---

### Post by zenon212 on 2007-05-13
I, too, am having this problem.  It seems that in my case, I installed Ubuntu CE, so I could get  Dansguardian already setup with the GUI and everything seemed to be working fine.  It was blocking everything that I wanted it to block by default.

Then, and I don't know if this is related, I setup my wireless through Ndiswrapper.  I had to turn it off a few times because I needed to download my cards drivers, but all I did was push buttons on the Basic screen.

Then I went and set everything back the way it was.  And from that point on, when Dansguardian is disabled I cannot connect to the web at all.  But if it is enabled and I lock Firefox, Firefox will always change to "Direct Connection to the Internet".

---

### Post by mhancoc7 on 2007-05-14
> **zenon212 said:**
> I, too, am having this problem.  It seems that in my case, I installed Ubuntu CE, so I could get  Dansguardian already setup with the GUI and everything seemed to be working fine.  It was blocking everything that I wanted it to block by default.

Then, and I don't know if this is related, I setup my wireless through Ndiswrapper.  I had to turn it off a few times because I needed to download my cards drivers, but all I did was push buttons on the Basic screen.

Then I went and set everything back the way it was.  And from that point on, when Dansguardian is disabled I cannot connect to the web at all.  But if it is enabled and I lock Firefox, Firefox will always change to "Direct Connection to the Internet".

It sounds like a proxy settings issue to me. You can use the GUI to unlick your firefox settings independent of the filter settings.

Jereme

---

### Post by zenon212 on 2007-05-14
> **mhancoc7 said:**
> It sounds like a proxy settings issue to me. You can use the GUI to unlick your firefox settings independent of the filter settings.

Jereme

That may be true and I will look into it.  But I haven't changed any of the proxy settings from the CE installation defaults.  All that I did with regard to my filter/proxy/Interent settings is what I mentioned before.

---

### Post by zenon212 on 2007-05-14
New info:

With Dansguardian set to Firefox Unlocked, if I go into the settings on Firefox and change from Direct Connection to Manual Proxy Configuration and then click OK and go back in, then it is set to Manual.  No big surprise there.  But if I shut Firefox down and then reopen it and go back to the settings, it is set back to Direct Connection again.

---

### Post by Yaka on 2007-05-15
i am on Ubuntu feisty, same problem with the first poster as well.

anyone know if dan guardian works with other browser like opera?

---

### Post by zenon212 on 2007-05-16
Well, I found my problem.  I hope this helps somebody else.

So I found the file /usr/lib/firefox/firefox.config and the only line in it was:

[INDENT]lockPref("network.proxy.type", 0);[/INDENT]

...which of course is to set it to "Direct Connection".  So I changed the 0 to a 1, for Manual and then saved it and opened Firefox.  Lo and behold, it stayed.

Then I shut it down and opened up Dansguardian and pressed the Firefox Lock button and opened Firefox again and it was set back to "Direct Connection".  So I changed the file again and it now stays.

I tested it a few times and it seems that the Dansguardian GUI resets that file to the above mentioned setting every time I lock or unlock Firefox.

I will just create a configuration file the way I want it and just copy it over whenever I need to lock or unlock Firefox.  That should not be too often since this is my 9 year-old's computer.

---

### Post by mhancoc7 on 2007-05-16
> **zenon212 said:**
> Well, I found my problem.  I hope this helps somebody else.

So I found the file /usr/lib/firefox/firefox.config and the only line in it was:
[INDENT]lockPref("network.proxy.type", 0);[/INDENT]...which of course is to set it to "Direct Connection".  So I changed the 0 to a 1, for Manual and then saved it and opened Firefox.  Lo and behold, it stayed.

Then I shut it down and opened up Dansguardian and pressed the Firefox Lock button and opened Firefox again and it was set back to "Direct Connection".  So I changed the file again and it now stays.

I tested it a few times and it seems that the Dansguardian GUI resets that file to the above mentioned setting every time I lock or unlock Firefox.

I will just create a configuration file the way I want it and just copy it over whenever I need to lock or unlock Firefox.  That should not be too often since this is my 9 year-old's computer.

Thanks, I have been watching this thread closely. I have fixed the issue and it will be ready for the next release.

Jereme

---

### Post by Yaka on 2007-05-16
i have tired this and i cant edit the config file  but follwing the rest of the guide it works  until ii just type in url not suitable for kids and it loads up the site without a problem, when i thought it would bring up the normals dans guardian blocked image. 

i am i doing something wrong?

i am a newbie when it comes to dansguardian but i thought after this it would block pages

---

### Post by mhancoc7 on 2007-05-16
> **Yaka said:**
> i have tired this it works but i have problem still, lets say i just type in url not suitable for kids and it loads up the site without a problem, when i thought it would bring up the normals dans guardian blocked image. 

i am i doing something wrong?

i am a newbie when it comes to dansguardian but i thought after this it would block pages

The current setup does not allow for a direct connection. If you use direct connection then the filter will not work. This bug will be fixed in the next release.

Jereme

---

### Post by Yaka on 2007-05-16
so how do i switch to auto detect? ive tried preety much everything suggested in this thread and nothing works. 
some random times it goes to manual but im not what settings i should use with manual

---

### Post by zenon212 on 2007-05-16
Yaka, If you are talking about switching to Auto Detect in that configuration file that I was talking about, then you would use the number 4.

[http://kb.mozillazine.org/Network.proxy.type]("http://kb.mozillazine.org/Network.proxy.type")

---

### Post by Yaka on 2007-05-16
ok but would you know why ubuntu wont let me edit it? save is greyed out and when i do save as it telles i cant edit it

---

### Post by zenon212 on 2007-05-16
If you want to edit it, then you have to do it as root.  I use gedit, so in a terminal I type

[INDENT]sudo gedit /usr/lib/firefox/firefox.config[/INDENT]

If I am really lazy then I will type

[INDENT]sudo nautilus[/INDENT]

...and then go find the file and open it.

sudo will ask you for the root password, which I think, if you are the only user account on the computer, will be your password.

---

### Post by zenon212 on 2007-05-16
> **mhancoc7 said:**
> Thanks, I have been watching this thread closely. I have fixed the issue and it will be ready for the next release.

Jereme

Glad I could help out.  :D

That is what I love about Linux--it has all the benefits of a major city with a small town feel.  Um, metaphorically, of course.

---

### Post by Yaka on 2007-05-16
ok its on auto detect, dans guardian is on ff locke and strictest setting enabled, when ever i enter in the a url from the ban list it still doesent get blocked:/

---

### Post by mhancoc7 on 2007-05-16
> **Yaka said:**
> ok its on auto detect, dans guardian is on ff locke and strictest setting enabled, when ever i enter in the a url from the ban list it still doesent get blocked:/

Try setting it to manual and use the following.

HTTP Proxy: 127.0.0.1
Port: 8080

If dansguardian is enabled then this should work.

I should have the next release with a fix for this in a few days.

Thanks, Jereme

---

### Post by mhancoc7 on 2007-05-17
We have just released Ubuntu CE v3.1 (Feisty). This should resolve the issues with dansguardian.

Announcement:
[http://ubuntuforums.org/showthread.php?t=447376](http://ubuntuforums.org/showthread.php?t=447376)

God Bless, Jereme

---

### Post by bricin on 2007-05-18
Got it!

Jereme, thanks for posting this script and fixing that last bug. The config is still a little odd in that sometimes the proxy server refuses a connection but in general this is blocking content (Opera and Firefox). But this solves one of the last remaining issues I have had with switching to Linux.

Sincerely,

Paul

---

### Post by mhancoc7 on 2007-05-18
> **bricin said:**
> Got it!

Jereme, thanks for posting this script and fixing that last bug. The config is still a little odd in that sometimes the proxy server refuses a connection but in general this is blocking content (Opera and Firefox). But this solves one of the last remaining issues I have had with switching to Linux.

Sincerely,

Paul

Glad you got it going. Let me know if you have any other troubles.

Thanks, Jereme

---

### Post by Tru on 2007-05-18
I have a fresh install of Ubuntu CE 3.0.  I actually have a few of them, but anytime I go into you dansguardian frontend and make any change I can not connect to the internet.  I also just ran your new upgrade script 3.1 on a almost fresh install with nothing done to it and still the same thing I try to change the filtering to moderate, then do a save and exit or anything for that matter and it I can no longer get to the internet.  This is pretty frustrating!  I have manually set the proxy in firefox, set it to auto detect still to no avail.  What gives with dansguardian?  What is the point of having it on if I have to disable it just to surf the web.  Doing something as simple as changing the filter level should not break this software.  I run a linux firewall with a proxy and url filter at work and never experience the diffuculty that I have with your integration of dansgaurdian.  I have this same problem on machines at work as well as at home which is not behind a proxy.  I did notice when the 3.1 script was installing some errors about dansguardian and when it was done I had 2 broken packages.  Clamav and tinyproxy, has anyone else had this problem?

---

### Post by mhancoc7 on 2007-05-18
> **Tru said:**
> I have a fresh install of Ubuntu CE 3.0.  I actually have a few of them, but anytime I go into you dansguardian frontend and make any change I can not connect to the internet.  I also just ran your new upgrade script 3.1 on a almost fresh install with nothing done to it and still the same thing I try to change the filtering to moderate, then do a save and exit or anything for that matter and it I can no longer get to the internet.  This is pretty frustrating!  I have manually set the proxy in firefox, set it to auto detect still to no avail.  What gives with dansguardian?  What is the point of having it on if I have to disable it just to surf the web.  Doing something as simple as changing the filter level should not break this software.  I run a linux firewall with a proxy and url filter at work and never experience the diffuculty that I have with your integration of dansgaurdian.  I have this same problem on machines at work as well as at home which is not behind a proxy.  I did notice when the 3.1 script was installing some errors about dansguardian and when it was done I had 2 broken packages.  Clamav and tinyproxy, has anyone else had this problem?

I am very sorry for your trouble. I am not sure why you have broken packages. I use Ubuntu CE on my own system with no troubles. The bugs that were found have been fixed. I will continue to watch this thread. I am always trying to make GUI better. This is the first major issue that has come up. I have already received confirmation that the update has fixed the issues with dansguardian for other users. 

Please keep me updated on how things progress for you.

God Bless, Jereme

---

### Post by Tru on 2007-05-18
I will try and run the 3.1 script again and see if I get those errors about dansguardian so I can post them.  I am just very frustrated with it at this point.  I am not a programmer, but I am a system administrator and do have knowledge of linux, proxies, firewalls, etc.....  So to have something like Dansguardian give me a problem every time I do something with it is making me mad.  Like I said I have it installed multiple times and it has never once worked right.  I even tried to uninstall it and that broke everything.  I could no longer install anything every time I did I got errors.  So, I reformatted and still anytime I made a basic change thru the GUI I could not connect to the internet.  I thought this was because I was behind my work proxy, but I installed it at home with the same problem.

I will try to rerun the 3.1 script this weekend and see if I can get you any info that is helpful besides my complaints :P

Thank you,
Andrew

---

### Post by mhancoc7 on 2007-05-18
> **Tru said:**
> I will try and run the 3.1 script again and see if I get those errors about dansguardian so I can post them.  I am just very frustrated with it at this point.  I am not a programmer, but I am a system administrator and do have knowledge of linux, proxies, firewalls, etc.....  So to have something like Dansguardian give me a problem every time I do something with it is making me mad.  Like I said I have it installed multiple times and it has never once worked right.  I even tried to uninstall it and that broke everything.  I could no longer install anything every time I did I got errors.  So, I reformatted and still anytime I made a basic change thru the GUI I could not connect to the internet.  I thought this was because I was behind my work proxy, but I installed it at home with the same problem.

I will try to rerun the 3.1 script this weekend and see if I can get you any info that is helpful besides my complaints :P

Thank you,
Andrew

Thanks, let me know how it goes. 

Jereme

---

### Post by Yaka on 2007-05-19
thanks for the update mate, shall try it later on tonite

---

### Post by Tru on 2007-05-21
Ok, I ran the new 3.1 script at work on one of my virtuals and I did not get any errors during the upgrade process, but anytime I make a change to the dans gui and hit save and exit I get a crash report that says gbx crashed.  I am not sure what that is, but I am still able to browse the web after a save and exit, but under firefox it shows direct connect and grayed out. Not sure if this is fine and dans is filtering since my work proxy blocks everything it would anyways.  I will try the upgrade script tonight at home and see if dans kills my internet again.

Thank you.

---

### Post by mhancoc7 on 2007-05-21
> **Tru said:**
> Ok, I ran the new 3.1 script at work on one of my virtuals and I did not get any errors during the upgrade process, but anytime I make a change to the dans gui and hit save and exit I get a crash report that says gbx crashed.  I am not sure what that is, but I am still able to browse the web after a save and exit, but under firefox it shows direct connect and grayed out. Not sure if this is fine and dans is filtering since my work proxy blocks everything it would anyways.  I will try the upgrade script tonight at home and see if dans kills my internet again.

Thank you.

Sounds like you may have it working now.

The gbx crash message can be safely ignored. It is related to the dansguardian GUI closing. I am working to get it resolved.

I look forward to hearing about your gome system. I appreciate your help with findinf and fixing these bugs.

Thanks, Jereme

---

### Post by Yaka on 2007-05-21
well having just tried the new script, i still have issues, after installing i did enable dans guardian then lock Firefox and save and exit. it worked fine with my login but when i tried one the children's logins FF came with the same proxy error. when i logged back in with my account i got the same proxy error as well

---

### Post by jonathonblake on 2007-05-23
>  got the same proxy error as well

a) Is your proxy running?
b) Is Firefox connecting to the proxy at the right port?

When i was getting a proxy error message, I found that my proxy wasn't running, so I had to manually start that, they I found Firefox wasn't correctly detecting the port the proxy was using.   So i corrected that.  [Both corrections were made somewhere in  config.d.

xan

jonathon

---

### Post by Yaka on 2007-05-24
well i am still having the same problems as before even when using the latest script, 

i am a preetuy much a n00b as ive only been using ubuntu for 2  months, but getting dans guardian up and running either via this script or via other methods has been the hardest task for me

---

### Post by mtennant on 2007-06-01
This is my first post.

I have used the DansGuardian script to install DG on a freshly updated 7.04 system (not CE) and have experienced all the same problems described here.

The simple act of using the DG GUI to make any kind of a change to DG causes it to break my Internet connection.

The only way to fix it is to run the DG install script again and then simply leave the DG GUI alone.

I know DG uses lots of pieces of code and various packages.

Has anyone seen these posts regarding firehol?

[http://ubuntuforums.org/showthread.php?t=456362](http://ubuntuforums.org/showthread.php?t=456362)

[https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/22](https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/22)

Could the problems with DG be related to these firehol bugs?

---

### Post by mhancoc7 on 2007-06-01
> **mtennant said:**
> This is my first post.

I have used the DansGuardian script to install DG on a freshly updated 7.04 system (not CE) and have experienced all the same problems described here.

The simple act of using the DG GUI to make any kind of a change to DG causes it to break my Internet connection.

The only way to fix it is to run the DG install script again and then simply leave the DG GUI alone.

I know DG uses lots of pieces of code and various packages.

Has anyone seen these posts regarding firehol?

[http://ubuntuforums.org/showthread.php?t=456362](http://ubuntuforums.org/showthread.php?t=456362)

[https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/22](https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/22)

Could the problems with DG be related to these firehol bugs?

Yes, the latest script should have fixed this. It adjusts the firehol configuration using a work around for that bug. I am not sure why there are still some who are having trouble. It is hard to figure out since so many are using it with no issues.

Thanks, Jereme

---

### Post by mtennant on 2007-06-01
I can only imagine this is a source of grief for you, as it is for us.

The only other thing I can think of is my networking setup.

I have an RT2500 based wireless card that I had to tweak to run properly under 7.04 (a file edit to support WPA).  

It acts strange in that it connects to my router properly, but I get a message that it has connected to the WIRED network when the system boots.

Could this be a contributing issue?

---

### Post by mhancoc7 on 2007-06-01
> **mtennant said:**
> I can only imagine this is a source of grief for you, as it is for us.

The only other thing I can think of is my networking setup.

I have an RT2500 based wireless card that I had to tweak to run properly under 7.04 (a file edit to support WPA).  

It acts strange in that it connects to my router properly, but I get a message that it has connected to the WIRED network when the system boots.

Could this be a contributing issue?

Maybe?

I noticed that you said, "
The only way to fix it is to run the DG install script again and then simply leave the DG GUI alone." Does this mean that the filter works until you use the GUI to tweak it?

Jereme

---

### Post by mtennant on 2007-06-01
Yes, that is my experience.

Leave it alone after it installs and you have no problems and the website blocking works fine.

Once you touch the GUI, goodbye Internet.

---

### Post by mtennant on 2007-06-01
I tested this on another machine running Christian Edition 7.04 that had been upgraded using the CONVERT script.

The behavior is the same.  This machine has no wireless, only Ethernet, so I guess that rules out the wireless angle mentioned above.

---

### Post by mhancoc7 on 2007-06-01
> **mtennant said:**
> Yes, that is my experience.

Leave it alone after it installs and you have no problems and the website blocking works fine.

Once you touch the GUI, goodbye Internet.

> **mtennant said:**
> I tested this on another machine running Christian Edition 7.04 that had been upgraded using the CONVERT script.

The behavior is the same.  This machine has no wireless, only Ethernet, so I guess that rules out the wireless angle mentioned above.

This is just bizarre. Please keep me updated on your progress.

You might try to download the Dansguardian script again and re-run it just to be absolutely sure you have the latest release. 

Jereme

---

### Post by mtennant on 2007-06-02
Jereme, 

Is there a special sequence you must go through to change the GUI settings in DG?

For example, must you turn it off and turn off the proxy lock before making changes, and then turn everything back on again and save?

Marty

---

### Post by mhancoc7 on 2007-06-03
> **mtennant said:**
> Jereme, 

Is there a special sequence you must go through to change the GUI settings in DG?

For example, must you turn it off and turn off the proxy lock before making changes, and then turn everything back on again and save?

Marty

No, you should be able to make the changes with it enabled. Then just be sure to click Save & Exit and then restart your browser.

Jereme

---

### Post by tbrunk1 on 2007-06-07
I have been following this discussion with interest because I am experiencing the same problems! I have Ubuntu CE installed on two machines. One at home and one in my ministries office. The one at the office has experienced no problems whatsoever! BUT... the one at home has nothing but problems with CE. I am guessing that it is a firehol problem that is unique to certain hardware configurations. I used the same install disk on BOTH machines, so the software is the same version (the newest one). 

On my home machine, I ended up changing the instalation to a plain (non-CE) Ubuntu instalation, then ran the CE script. Everything worked ok untill I used the parental control panel...Poof! Internet gone, same old problems. Then I reinstalled the non-CE Ubuntu and manually installed Dansguardian, Tinyproxy, and Firehol (no CE control panel)... ran for awhile then started experiencing problems again. So... I unstalled all three, then reinstalled ONLY Dansguardian and Tinyproxy, manually editing my dansguardian config files to my needs. I then locked out the Firefox proxy settings, forcing data to go through Dansguardian / Tinyproxy. I'm now going on a week with almost no problems... I say almost because every once in a awhile the proxy refuses connections. If I wait a minute and restart firefox the problem goes away. 

I have to believe this is some sort of hardware / firehol / tinyproxy conflict, but have no idea how to pin it down further. My uptime with this setup is about 98%...

---

### Post by Yaka on 2007-06-07
any chance you could pint us the guide u used for DG/tinyproxy install mate?

---

### Post by tbrunk1 on 2007-06-07
I used these instructions:

[http://ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian](http://ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian)

I just ignored the part concerning Firehol since it seems to be the main problem. Firehol forces trafic through the  proxy which can be done in Firefox anyway. If you lock the firefox settings, and not install another browser, then you end up filtering everything. 

Another good approach I found on setting up Dansguardian can be found here:
[http://www.vollmar.ch/dansguardian-e.html](http://www.vollmar.ch/dansguardian-e.html)

---

### Post by mtennant on 2007-06-08
I'm so glad this thread is still alive and has potential solutions.

I'll give your approach a try.

---

### Post by ericd8027 on 2007-06-20
I am a noob to Ubuntu CE as I recently converted from XP.  Once it was completely installed with all of the most up to date programs and scripts i have had internet connection problems after i ENABLED dg for the first time.  Since then, whenever I launch ff from the main screen i get errors saying I have no internet connection, even though I am connected to our intranet.  Even with changing the proxy settings there have been no improvements.  Now, if I launch ff through the DG GUI I am able to surf the web no problem.  I do not know if it is filtering or not as I have not tried to reach any of "those" sites.  If I save and close the DG GUI with the proxy locked OR unlocked, I return to having no internet connection when launching ff outside of the GUI.  The ONLY solution that I have found to this point is to continually launching ff through the dg gui which is frustrating and annoying.  Have I just missed the solution in this board or is there something else going on?

---

### Post by Tru on 2007-06-20
I finally just uninstalled dansguardian and tiny proxy.  Everytime I make a change and save and exit I can not get to the internet.  I have had this same problem on a couple different machines on 2 different networks.  Even with the latest convert script I have the same problem.  I will just run ipcop with advance proxy and url filiter on my network.  That always works and provides a very good firewall.

---

### Post by NeilBlanchard on 2007-06-25
Greetings,

I installed this, and I cannot find where to run it to set it up?  And I cannot get on the Internet at all... :(

If I cannot get it working, how can I uninstall it, and worst case -- do I have to reinstall Feisty?

[Edit: Nevermind -- I had not extracted the uninstaller.  I uninstalled it successfully.]

---

### Post by ericd8027 on 2007-07-12
So I installed Ubuntu CE and was having problems with dansguardian, firehol or tinyproxy or any combination there of.  After a while, ubuntu forced me to uninstall some stuff.  Over 2 weeks ago.  I have been trying to install dansguardian, purge it, or something.  Every time I type sudo apt-get install dansguardian tinyproxy firehol it comes up with the following error.  

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package dansguardian is not available, but is refereed to by another package. 
This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package dansguardian has no installation candidate

PLEASE HELP!!!

---

### Post by wtholt on 2007-07-13
I had trouble with the Dansguardian set up when added to my feisty setup. I removed and  used the CE convert script and still couldn't get it to work.  Yesterday I did a clean install of feisty and used the CE  "popular package" script for adding dansguardian, tiny proxy, firehol, and the GUI to regular feisty.  
I assume everything is latest edidtions, but the GUI is resetting firefog.cfg to **lockpref("network.proxy.type",0);** when I lock fireox.  Is there a way to edit something in the GUI configuration so it will write in  **lockpref("network.proxy.type",1);** instead?  or is there a patch I can use to fix the GUI?  Web access works when ever I unlock, but It would be nice to be able to lock and unlock easily as designed.

---

### Post by mhancoc7 on 2007-07-13
> **wtholt said:**
> I had trouble with the Dansguardian set up when added to my feisty setup. I removed and  used the CE convert script and still couldn't get it to work.  Yesterday I did a clean install of feisty and used the CE  "popular package" script for adding dansguardian, tiny proxy, firehol, and the GUI to regular feisty.  
I assume everything is latest edidtions, but the GUI is resetting firefog.cfg to **lockpref("network.proxy.type",0);** when I lock fireox.  Is there a way to edit something in the GUI configuration so it will write in  **lockpref("network.proxy.type",1);** instead?  or is there a patch I can use to fix the GUI?  Web access works when ever I unlock, but It would be nice to be able to lock and unlock easily as designed.

The current design of the GUI is to lock the Firefox proxy to Direct Connection. This ensures that the filtering is set since it is configured for transparent proxy filtering. If the user needs to use a specific proxy setup then they can unlock it.

In the future I may incorporate additional options for locking the settings in different ways.

Thanks, Jereme

---

### Post by wtholt on 2007-07-13
Thanks for the quick reply.  I am new to Ubuntu, played aroung with several different linux distros through the years but until now have not found one that I like the "feel" of the desktop--Ubuntu has done well with this and am wanting to move the family to it--dansguargian is a must for this to happen--so thank so much to you and all those who have worked so hard to make it accessable.

I changed the firefox settings to manual proxy settings (read it somewhere)  after I reinstalled everything yesterday because I couldn't get to the web initially after that obligatory reboot.  Changing to manual proxy actually didn't seem to help so I checked all the config files for the three packages and they where fine, restarted tinyproxy, restarted firehol and ran the pakage reconfigure thing for dansguardian after that  I could get to the web until I re-locked.  Checked out what lock / unlock was doing in the firefox.cfg so I found out it was forcing direct connect. Could not get to the web that way.

I'll set the firefox preferances to  direct connect when I get home and see if it will work that way now that everything has been restarted...  If the firefox.cfg overrides the setting inside  firefox preferances then there will still be a problem because with ** lockpref("network.proxy.type",0); ** I get the infamous proxy error.

---

### Post by wtholt on 2007-07-13
Set Firefox Preferences back to "direct Connection to the internet".  I can get it to reach the internet, but I have to restart dansguardian any time I lock or unlock using the GUI.  (at the prompt in terminal "**Sudo /etc/init.d/dansguardian restart**.   It's ok with me, at least dansguardian is filtering and I can get to the internet--still easier to use the GUI to adjust things.  It may turn out to be a hardware problem, or something with the wireless card.  If so it may be an option on a future release to have a check-box in the gui that can be checked to "restart Dansguardian on exit."   It would save the user some steps.

---

### Post by cafluegg on 2007-07-14
> **wtholt said:**
> Set Firefox Preferences back to "direct Connection to the internet".  I can get it to reach the internet, but I have to restart dansguardian any time I lock or unlock using the GUI.  (at the prompt in terminal "**Sudo /etc/init.d/dansguardian restart**.   It's ok with me, at least dansguardian is filtering and I can get to the internet--still easier to use the GUI to adjust things.  It may turn out to be a hardware problem, or something with the wireless card.  If so it may be an option on a future release to have a check-box in the gui that can be checked to "restart Dansguardian on exit."   It would save the user some steps.

I believe that this is my first post here on these forums.

I read this whole thread through, as I was having difficulties getting DG up and running.

I too, experienced internet breakage every time I would save and exit the DG GUI. Restarting DG in a terminal window fixed my internet. I'm glad I read this thread because - although it make sense now - I would have never thought to restart DG. BTW, it should be lower case sudo; not upper case, as is shown in the above post.

I believe, however, that  wtholt has hit the nail on the head here when he suggests a check-box to "restart DG" on exit. This would simplify things immensely.

Thanks Jereme for a great Distro!

One question, is there a 64 bit version? Thanks again.

---

### Post by cafluegg on 2007-07-15
I noticed something else...

I installed xubuntu-desktop last night, with the intention of removing the gnome environment. I decided, however, to put xubuntu through it's paces before removing gnome. In doing so, I noticed that DG would break quite frequently. I had to restart DG about five times over a period of three to four hours. As a result, I decided to stay in gnome for the time being.

Any idea why this would happen? Would uninstalling gnome fix the problem?

Thanks

---

