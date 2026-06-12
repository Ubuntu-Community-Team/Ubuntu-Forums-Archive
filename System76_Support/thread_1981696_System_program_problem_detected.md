---
title: "System program problem detected"
date: 2012-05-17
forum: System76 Support
---

### Post by Maxence on 2012-05-17
Helle there,

I have a problem since I updated the ubuntu version from 11.04 to 12.04. When I start the computer, I have an error message saying: "System program problem detected - Do you want to report the problem now?" Sometimes, the PC starts the secure mode. 
How can I know where the problem comes from?

Thank you very much!!!
max

---

### Post by isantop on 2012-05-17
What method did you use to upgrade? Did you do an online upgrade? If so, did you go directly to 12.04 form 11.04?

---

### Post by clucas on 2012-05-17
I have the same problem and did the online upgrade and went from 11.10 to 12.04.

---

### Post by MoebusNet on 2012-05-18
I upgraded from 11.10 to 12.04 and within a few days and a few updates had the same problem. However, I no longer get the "system problem" message since my last batch of updates. May I suggest that you make sure that you have all available updates installed? Just a suggestion...best of luck.

---

### Post by Maxence on 2012-05-20
i used the update manager to go directly from 11.04 to 12.04. But actually since I did the latest updates, the message doesn't appear any more. 
Thanks for the help. if it appears again, i'll come back to you isantop!
regards,

---

### Post by scowby on 2012-05-24
I get this same error message but I installed completely fresh Ubuntu 12.04.  There was no upgrade process and the error message did not start popping up until recently.

Any ideas?

-= The Space Cowboy =-
[http://mycamcar.com](http://mycamcar.com)

---

### Post by isantop on 2012-05-24
> **scowby said:**
> I get this same error message but I installed completely fresh Ubuntu 12.04.  There was no upgrade process and the error message did not start popping up until recently.

Any ideas?

-= The Space Cowboy =-
[http://mycamcar.com](http://mycamcar.com)

Does it happen frequently? I would report the error, and move on from there. This has the added benefit of checking to see if it's the same problem every time. If they're all different problems, then it's probably environmental.

---

### Post by oldmankit on 2012-06-01
> **isantop said:**
> Does it happen frequently? I would report the error, and move on from there. This has the added benefit of checking to see if it's the same problem every time. If they're all different problems, then it's probably environmental.

I have clicked the "report problem" button several times.

I did a fresh install of 12.04 from CD.  I have been updating regularly in the hope that this problem get solved.

It pops up after boot time, and at seemingly random intervals (every few hours?) whilst using Ubuntu.

---

### Post by miskopo on 2012-06-03
It happens to me, too.
I have fresh CD install of Pangolin and I get this error even 5 times a minute.

---

### Post by tgrego on 2012-06-03
same problem here.. its a bit annoying...
tried to run "sudo rm /var/crash/*" because I saw that as a possible solution, but no luck, it still pops up frequently.

Also I think it got worse right after I installed and set uo mythtv... can mythtv be a cause? I don't really wat to remove mythtv to test it cause it was a pain to get working properly...

---

### Post by MoebusNet on 2012-06-03
After my post above, I started getting the "system program problem" message again. I've attached my error message.

Mine has to do with 'colord', which according to launchpad has an oustanding bug for about 6 months marked 'low priority'. Maybe if enough people submit the crash reports we'll see something happen.

---

### Post by oldmankit on 2012-06-04
I found that 
"sudo rm */var/crash/**"
seems to have fixed it for me.  We must be dealing with different problems since this hasn't fixed it for some people.

---

### Post by Billy Greenacre on 2012-06-05
I have been having the same problem. First, I get a message that says, *"System program problem detected. Do you want to report the problem now?"* Then it has two buttons.  One of which reads, "*Cancel*" the other reads "*Report problem*." 
 
Clicking on the *Cancel* button collapses the message window. Clicking on "*Report Problem"* brings up a different window which reads, *"Please enter your password to access problem reports of system programs."  *This is followed by two buttons, the first of which reads, "*Cancel*" and the other reads "*OK*". 
 
When the *CANCEL*  button is clicked, the message window disappears.  If you click on the *OK* button without entering a password, it repeats the request. 
 
I find this alarming. It seems to a rather too obvious attempt on someone's part to get my password(s).  This machine is a brand new 64 bit box with a long list of hardware in it. I had trouble installing Ubuntu for a couple of weeks, but this started happening once I finally got Ubuntu 12.04 installed.

I have uploaded a screen shot of the first window you get when the message first appears. It is impossible to get a screen shot of the second window.

 I am also having trouble with intermittent freezes that do not respond to any keyboard or mouse input.  The trick of using CNTRL-ALT-F1 to get a terminal window up and bypassing Ubuntu's GUI does not work, because it does not listen to any input from the keyboard.
 
I at first thought the freeze problem was related to Flash or the Flash plug-in for Firefoxe, but it occurs when I am doing something other than playing videos or music.

---

### Post by BudBear on 2012-06-05
> **Billy Greenacre said:**
> I have been having the same problem. First, I get a message that says, *"System program problem detected. Do you want to report the problem now?"* Then it has two buttons.  One of which reads, "*Cancel*" the other reads "*Report problem*." 
 
Clicking on the *Cancel* button collapses the message window. Clicking on "*Report Problem"* brings up a different window which reads, *"Please enter your password to access problem reports of system programs."  *This is followed by two buttons, the first of which reads, "*Cancel*" and the other reads "*OK*". 
 
When the *CANCEL*  button is clicked, the message window disappears.  If you click on the *OK* button without entering a password, it repeats the request. 
 
I find this alarming. It seems to a rather too obvious attempt on someone's part to get my password(s).  This machine is a brand new 64 bit box with a long list of hardware in it. I had trouble installing Ubuntu for a couple of weeks, but this started happening once I finally got Ubuntu 12.04 installed.

I have uploaded a screen shot of the first window you get when the message first appears. It is impossible to get a screen shot of the second window.

 I am also having trouble with intermittent freezes that do not respond to any keyboard or mouse input.  The trick of using CNTRL-ALT-F1 to get a terminal window up and bypassing Ubuntu's GUI does not work, because it does not listen to any input from the keyboard.
 
I at first thought the freeze problem was related to Flash or the Flash plug-in for Firefoxe, but it occurs when I am doing something other than playing videos or music.


this exact thing just started happening on my puter.  i did  a fresh install back in April and 12.04 has been ok, a few things here and there most of which i was able to smooth out.  

but i agree Billy, this seems odd. i mean what password does it want me to enter? 

i will try the updates, i believe there is a kernel update for my pc.  i like to wait on those incase there are issues.  i doubt clamav and rkhunter will detect anything, but i'll try that too.

---

### Post by BudBear on 2012-06-05
nothing found,
cleared /var/crash
and did all avail updates. rebooted and no more error.
can't be sure what the cause was, so i'm subscribing to this thread in case it comes back.

---

### Post by deadflowr on 2012-06-05
System crash detected reports can be very annoying. Especially when nothing seems to be going wrong. the current state of system problems detected probably goes to the fact that apport has been enabled in 12.04. It is very simple to disable just edit the file 
/etc/default/apport, and change the enabled setting from enable=1 to enable-0 then save.

Although, if things aren't peachy, it might be good to keep it enabled.

I personally find the error-tracking tools to be pretty triggerhappy.

---

### Post by bilbo.san on 2012-06-06
I have the same issue here... I have the impression that this started since I accidentally left a movie DVD inside the laptop, next morning, the error started to come up. 
I am running a fresh install Ubuntu 12.04

I agree with some of you, it looks like if someone is trying to hack-in.

Has anyone been able to fix this problem?

---

### Post by Billy Greenacre on 2012-06-06
I just had another very odd thing happen.  I tried to get the updates for my system, I have the updater set to update on a daily basis, the system came back with a message that read, "*Waiting for apt-get to exit."* I got up to go get a drink of water. When I got back the machine said something like "Could not remove package." Unfortunately, being rum-drum I did not think to get a screenshot of this message and clicked on either an *OK* button or a *CANCEL* button, which made the message disappear. The window behind it, was the update window, so I clicked on the *UPDATE* button and it downloaded several GUI related upgrades. 
 
While the behavior of this machine has become more mysterious, so far so good.

---

### Post by bilbo.san on 2012-06-06
I really really think it is a Flash-plugin related thing. I had some problem removing it in an older version or Ubuntu, and just yesterday, when visiting a website with a flash video, it crashed like 3 times and gave me the same System Program problem notice.

When checking into the installed programs, and clicking on Flash Plugin, the same thing again. But beyond that, the system is running just fine.

I wish there could be some sort of solution by the developers or anyone in the community.

---

### Post by brdmn on 2012-06-06
> **Billy Greenacre said:**
> I just had another very odd thing happen.  I tried to get the updates for my system, I have the updater set to update on a daily basis, the system came back with a message that read, "*Waiting for apt-get to exit."* 

I think this has to do with the automated update system, which is running in the background and using apt-get.  If it happens to be running at the moment you launch the GUI update tool, the message pops up.

---

### Post by MoebusNet on 2012-06-09
> **Billy Greenacre said:**
> I find this alarming. It seems to a rather too obvious attempt on someone's part to get my password(s).

Just in case you weren't aware, Ubuntu is designed so that most activities are performed at a user level, which means that you cannot perform out-of-the-ordinary functions like update software, modify system files or view certain files without administrative privileges. While many Linux OS's do that by logging out as the user and logging in as administrator (called 'root' in Linux), Ubuntu allows you to upgrade the user privileges to admin privileges if you posess the admin password. That is why you will be asked for your password; it prevents external programs from performing unauthorised actions on your system. In Terminal, to activate administrative privileges, you prefix the command 'sudo' to whatever commands you issue. Then you will be asked for your password.


Security in Ubuntu is pretty good, so I doubt that this was an instance of malware fishing for your password. That said, there is always a small chance that this can occur. I just haven't seen it or heard of it on the forum.

---

### Post by handle1790 on 2012-06-11
I have to agree with the complaints here.  When this pops up, I'm generally on a web browser and it looks like a phishing scam.

No matter how good security is, many people use linux because they tend to be paranoid about internet security. My heart certainly started pounding when it popped up.  It's just not professional.

---

### Post by flurdy on 2012-06-14
> **handle1790 said:**
> I have to agree with the complaints here.  When this pops up, I'm generally on a web browser and it looks like a phishing scam.

No matter how good security is, many people use linux because they tend to be paranoid about internet security. My heart certainly started pounding when it popped up.  It's just not professional.

Ditto. Popped up when I had Chrome open. I assumed it was a phishing scam, that some clever bugger had detected I was running Ubuntu and skinned the fake window with gtk etc. 

The steps just seemed like a classic phishing attack. First a big alert that some thing critically wrong has happened (with no detail) and next screen is to enter my password for no apparent reason.

---

### Post by isantop on 2012-06-14
> **flurdy said:**
> Ditto. Popped up when I had Chrome open. I assumed it was a phishing scam, that some clever bugger had detected I was running Ubuntu and skinned the fake window with gtk etc. 

The steps just seemed like a classic phishing attack. First a big alert that some thing critically wrong has happened (with no detail) and next screen is to enter my password for no apparent reason.

Again, that is a standard Ubuntu error dialog, and it's perfectly fine to proceed from there. 

In 12.04, they've left the crash reporter on instead of disabling shortly before release. These crashes are normal and happen all the time, and the system usually cleanly recovers. In previous releases, these still happened, but they were hidden from the user. For whatever reason, Canonical has decided to leave them on in 12.04, thus the error messages.

---

### Post by colinmccubbin on 2012-06-15
I have a brand new panp9 picked up yesterday. I charged it up, ran through set-up, all good, wifi works. 

I plugged it into wired net, turned off wifi,  opened firefox, tried playing an mp3 from my own site, was told it needed a plugin, said ok, was told pluging installation had failed..

Before going any futher I thought to do a system  update and am told 'failed to download package files'.   apparently the .deb file is a 404 not found. 

I tried to shut the computer down, thinking to try again in the morning, it wouldn't shut down, just went to a login screen asking for my pw. I entered my pw and it went back to my desktop. I can only shut it down by holding the power button for 10 secs!! 

 
This morning, same problem with updating, and now it is throwing 'system program performace errors', as  per this thread.

I run earlier versions of Ubuntu and current version of Mint on 2 desktops, and having heard that installations on laptops can be tricky thought that buying from system 76 would guarantee a working system, I am really sadened to find so many problems with a brand new machine.

I will see if their technical support can talk me through the fixes, else it will be going back on Monday for a full refund.

Finally I can log onto their site using my order number but when I spent a long time filling in a service ticket I couldn't submit it, I keep geting a popup saying 'please fill in all fields'. There are only 2 fields, both are filled in..:confused: 

Hence I'm posting here.

---

### Post by isantop on 2012-06-15
> **colinmccubbin said:**
> I have a brand new panp9 picked up yesterday. I charged it up, ran through set-up, all good, wifi works. 

I plugged it into wired net, turned off wifi,  opened firefox, tried playing an mp3 from my own site, was told it needed a plugin, said ok, was told pluging installation had failed..

Before going any futher I thought to do a system  update and am told 'failed to download package files'.   apparently the .deb file is a 404 not found. 

I tried to shut the computer down, thinking to try again in the morning, it wouldn't shut down, just went to a login screen asking for my pw. I entered my pw and it went back to my desktop. I can only shut it down by holding the power button for 10 secs!! 

 
This morning, same problem with updating, and now it is throwing 'system program performace errors', as  per this thread.

I run earlier versions of Ubuntu and current version of Mint on 2 desktops, and having heard that installations on laptops can be tricky thought that buying from system 76 would guarantee a working system, I am really sadened to find so many problems with a brand new machine.

I will see if their technical support can talk me through the fixes, else it will be going back on Monday for a full refund.

Finally I can log onto their site using my order number but when I spent a long time filling in a service ticket I couldn't submit it, I keep geting a popup saying 'please fill in all fields'. There are only 2 fields, both are filled in..:confused: 

Hence I'm posting here.

It sounds like your packaging cache is outdated. Go ahead and open up the Update Manager application, then click "check" and wait for that to finish. Once it has, then try updating. 

As described above, the crash dialogs are not indicative of a problem, and you can safely ignore them.

---

### Post by LightningCrash on 2012-06-15
> **isantop said:**
> Again, that is a standard Ubuntu error dialog, and it's perfectly fine to proceed from there. 

In 12.04, they've left the crash reporter on instead of disabling shortly before release. These crashes are normal and happen all the time, and the system usually cleanly recovers. In previous releases, these still happened, but they were hidden from the user. For whatever reason, Canonical has decided to leave them on in 12.04, thus the error messages.

Maybe in 12.10 they should make it an opt-in feature the first time around.

---

### Post by colinmccubbin on 2012-06-16
> **isantop said:**
> It sounds like your packaging cache is outdated. Go ahead and open up the Update Manager application, then click "check" and wait for that to finish. Once it has, then try updating. 

As described above, the crash dialogs are not indicative of a problem, and you can safely ignore them.

Thanks... Before reading your reply, I tried again at about 8.10 am PST yesterday and the update ran, so either the updater was requesting a different file name, or the .deb  file it was requesting then existed on the server. Only hitch was half way through when the update stopped and told me that GRUB had previously been installed on a different disk, (presumably the parent disk at system76 from which mine had been cloned?) what did I want to do? I called tech support who told me which disk to install it to (2 were offered)  and it proceeded ok.:p

The shut down still doesn't work though, and although firefox no longer requests a plugin to play mp3s, the spot where the player should be in the web page is blank and no music plays. 

I haven't had time to delve into these, but will have time on Sunday..

Mahalo,

---

### Post by isantop on 2012-06-18
> **LightningCrash said:**
> Maybe in 12.10 they should make it an opt-in feature the first time around.

It has been opt-in in every previous release, and the opt-in method is technical and complex. Now, it's an opt-out using the same method. I can't say I agree with the direction on that.

---

### Post by Carborundum on 2012-06-18
> **isantop said:**
> It has been opt-in in every previous release, and the opt-in method is technical and complex. Now, it's an opt-out using the same method. I can't say I agree with the direction on that.
For the record, you can opt-out by running this command:
```
sudo sed -i s/enabled=1/enabled=0/ /etc/default/apport
```

---

### Post by MoebusNet on 2012-06-18
Thanks! Opted out.

---

### Post by isantop on 2012-06-19
> **Carborundum said:**
> For the record, you can opt-out by running this command:
```
sudo sed -i s/enabled=1/enabled=0/ /etc/default/apport
```

Whoa! That's sed!

(Er'body look out, we got a guru ovah here!) ;)

---

### Post by Billy Greenacre on 2012-06-20
Okay, Carborundum. I have loaded the terminal package and entered your commands. I will let you know if it works. 

I am still experiencing unexpected freezes. I have yet to nail it down for certain, but it seems to freeze whenever Firefox is up and online.  There are some web sites that will cause this machine to freeze while they are in the middle of loading.  Yahoo news is one, Fox News is the other. I installed a Firefox plug-in named Flashblock and this seemed to help a great deal, but it has not cured the problem entirely. I will post my results here when I get the chance.

---

### Post by Carborundum on 2012-06-20
> **Billy Greenacre said:**
> I am still experiencing unexpected freezes. I have yet to nail it down for certain, but it seems to freeze whenever Firefox is up and online.  There are some web sites that will cause this machine to freeze while they are in the middle of loading.  Yahoo news is one, Fox News is the other. I installed a Firefox plug-in named Flashblock and this seemed to help a great deal, but it has not cured the problem entirely. I will post my results here when I get the chance.
That sounds a lot like the problem described in bug [#993187]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187"). Never mind the "Won't Fix" status; that's just because the bug tracker became cluttered with lots of similar but unrelated bugs. For Sandy and Ivy Brigde, the fix is to upgrade to a newer kernel (3.3 or later).

---

### Post by Billy Greenacre on 2012-06-23
> **Carborundum said:**
> That sounds a lot like the problem described in bug [#993187]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187"). Never mind the "Won't Fix" status; that's just because the bug tracker became cluttered with lots of similar but unrelated bugs. For Sandy and Ivy Brigde, the fix is to upgrade to a newer kernel (3.3 or later).

I have not seen the **System Error Detected **message since I entered the code you posted. I am still having trouble with the **Random Freeze Problem**. This particular error is almost certainly related to Firefox in some way, because it mostly happens when I have Firefox up and running.  In fact, I cannot remember ever having it happen while I was offline. There are some sites where it happens almost as soon as the page loads.

Is Ubuntu susceptible to the **Fat Packet** attack?

---

### Post by Carborundum on 2012-06-24
> **Billy Greenacre said:**
> I am still having trouble with the **Random Freeze Problem**. This particular error is almost certainly related to Firefox in some way, because it mostly happens when I have Firefox up and running.  In fact, I cannot remember ever having it happen while I was offline. There are some sites where it happens almost as soon as the page loads.
Could it be related to Adobe Flash? That is what others who are experiencing a similar sounding problem are reporting.

Have you tried upgrading your kernel?

> Is Ubuntu susceptible to the **Fat Packet** attack?I don't know what that is.

---

### Post by Billy Greenacre on 2012-06-26
Yes, I do update my system every time an upgrade becomes available. 
 
Once upon a time, long ago in a very bad time, one could send  an overly large IP packet to a system running nearly any operating system. That packet would make the targeted system freeze, much like the freezes I am seeing with this system now.  The user-victim would have no choice but to do a hard reset of his or her hardware.
 
I have installed a plug-in called *Flashblock* that stops Flash videos from automatically running. It has helped some, but has not eliminated the problem. Even with the *Flashblock* plug-in installed and running, my system suddenly and inexplicably freezes at random moments with no way to know when it will occur.
 
It has only occurred while I was on this BBS while I had another tab open in Firefox running something that had a Flash file that ran auto matically. It very seldom freezes when I am visiting the Wikipedia, but does ofte happen while I am on my Yahoo homepage, or when I am on the Fox News site. It only recently started to happen on the Wikia site, usually when I am on the Steampunk pages. 

Using a **Fat Packet** attack on persons you do not like was, at one time, a very common practice on sundry political fora. I have not visited one of those kinds of fora for a long time now, (Waving old fart's badge) but I do remember that it was a common practice a decade or so ago.

---

### Post by isantop on 2012-06-26
> **Billy Greenacre said:**
> Yes, I do update my system every time an upgrade becomes available. 
 
Once upon a time, long ago in a very bad time, one could send  an overly large IP packet to a system running nearly any operating system. That packet would make the targeted system freeze, much like the freezes I am seeing with this system now.  The user-victim would have no choice but to do a hard reset of his or her hardware.
 
I have installed a plug-in called *Flashblock* that stops Flash videos from automatically running. It has helped some, but has not eliminated the problem. Even with the *Flashblock* plug-in installed and running, my system suddenly and inexplicably freezes at random moments with no way to know when it will occur.
 
It has only occurred while I was on this BBS while I had another tab open in Firefox running something that had a Flash file that ran auto matically. It very seldom freezes when I am visiting the Wikipedia, but does ofte happen while I am on my Yahoo homepage, or when I am on the Fox News site. It only recently started to happen on the Wikia site, usually when I am on the Steampunk pages. 

Using a **Fat Packet** attack on persons you do not like was, at one time, a very common practice on sundry political fora. I have not visited one of those kinds of fora for a long time now, (Waving old fart's badge) but I do remember that it was a common practice a decade or so ago.

The freezes on your system are being caused by a Kernel glitch related to the graphics driver. There will be an updated kernel available shortly.

---

### Post by Carborundum on 2012-06-26
> **Billy Greenacre said:**
> Yes, I do update my system every time an upgrade becomes available. 
Ah, but due to Ubuntu's rolling release system, that means you're not actually running the latest available kernel. Standard Ubuntu 12.04 is still using kernel 3.2.0, and this particular problem (or one very similar to it) wasn't fixed until kernel 3.3.6.

Before going any further, I should mention that System76 is aware of this problem, and will be posting an official solution soon (Edit: Ninja'd). However, if soon isn't soon enough for you, here is how to manually upgrade to a newer kernel (3.4 to be specific):

[LIST]
[*]Download the necessary packages for your architecture from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-precise/")
[LIST]
[*]For example, if you are running 64-bit Ubuntu (which is most likely the case, but double check to be sure), download '[linux-headers-3.4.0-030400-generic_3.4.0-030400.201205210521_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-precise/linux-headers-3.4.0-030400-generic_3.4.0-030400.201205210521_amd64.deb")', '[linux-headers-3.4.0-030400_3.4.0-030400.201205210521_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-precise/linux-headers-3.4.0-030400_3.4.0-030400.201205210521_all.deb")' and '[linux-image-3.4.0-030400-generic_3.4.0-030400.201205210521_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-precise/linux-image-3.4.0-030400-generic_3.4.0-030400.201205210521_amd64.deb")'.
[/LIST]
 
[*]Install them:
[/LIST]
```
sudo dpkg -i linux-headers-3.4.0-030400_3.4.0-030400.201205210521_all.deb
sudo dpkg -i linux-headers-3.4.0-030400-generic_3.4.0-030400.201205210521_amd64.deb
sudo dpkg -i linux-image-3.4.0-030400-generic_3.4.0-030400.201205210521_amd64.deb
```
[LIST]
[*]Reboot
[/LIST]
You should now be running kernel 3.4. Verify with ```
uname -a
```

---

### Post by Billy Greenacre on 2012-06-30
Wayul,  shuckins! Canonical came out with an update today. I let it install itself on my system. Guess what? Not only is the kernel still 3.2.0-26-generic #41, it made matters much worse! I can't stay online nearly as long as I could before the current update.  The system freezes shortly after I get online, every time. I'll be lucky to finish this message without a system freeze. 
 
I will give your suggestion a try, but I really think that Canonical should be a bit more responsive to these kinds of situations.  If they have a fix for the problem, why haven't they made it a part of the normal update?  I guarantee you that *Apple* would have already posted a fix as well as putting it in the update pipe.

---

### Post by Carborundum on 2012-07-01
> **Billy Greenacre said:**
> Wayul,  shuckins! Canonical came out with an update today. I let it install itself on my system. Guess what? Not only is the kernel still 3.2.0-26-generic #41, it made matters much worse! I can't stay online nearly as long as I could before the current update.  The system freezes shortly after I get online, every time. I'll be lucky to finish this message without a system freeze. 
 
I will give your suggestion a try, but I really think that Canonical should be a bit more responsive to these kinds of situations.  If they have a fix for the problem, why haven't they made it a part of the normal update?  I guarantee you that *Apple* would have already posted a fix as well as putting it in the update pipe.

I understand your frustration, but unfortunately it's not quite so simple as that. The problem is fixed in a later kernel, but it isn't clear which commits are responsible for fixing it. Before a patch to the current kernel can be made, the correct commits must be identified, and then backported without breaking anything else.

Check bug [#999910]("https://bugs.launchpad.net/ubuntu/precise/+source/linux/+bug/999910") to see how the work on this is progressing. If you read the comments, you will notice that Carl Richell (System76 CEO) is an active participant in trying to find a solution.

For what it's worth, people are reporting that the current proposed kernel (3.2.0-27.42) fixes the problem. It should go live in a matter of days, assuming nothing untoward happens.

---

### Post by Billy Greenacre on 2012-07-01
Okay, I finally got it to reboot after having installed the new kernel.  It now claims that it is: 3.4.0-030400-generic #201205210521 SMP Mon May 21 09:22:02 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux.
 
Unfortunately, it took several tries to reboot. I kept getting that little page whereon it offers to start up in recovery mode.  Being unadventurous and hammer-headed, I refused to let run through the safe mode. This proved to be a mistake. On one occasion, it ran some kind of listing for hours until I did a hard reset.  After that reset, I chose to have it boot in safe mode. It ran through several items, none of which I can now recall, and then gave me a page where it said something about rebooting in normal mode. It notified me that the graphic drivers would require a hard reset and if nothing happened after I clicked on the Okay button, I should do a hard reset-- or words to that effect. 
 
I clicked on the Okay button and it came right up, asking me for my password. I typed in my password and here I am, fat dumb and fearful.  I should have let it try to restart in protected mode the first time I rebooted the machine. I still do not know if it will reboot smoothly. I will now try it and return to this forum, if I can, and post the results of my next experiment with Precise Pangolin.

---

### Post by Billy Greenacre on 2012-07-01
Okay, Carborundum, now I know that it will only reboot in what it refers to as "protected mode".  This is distressing because I must first atttempt to boot the machine in normal mode before I can get the option to boot in "protected mode." 
 
I am hoping that it will suspend and return without a hitch so that I can simply suspend it and not shut the machine  down altogether. I will now go try it and return here to post the results.

---

### Post by Carborundum on 2012-07-01
> **Billy Greenacre said:**
> Okay, I finally got it to reboot after having installed the new kernel.  It now claims that it is: 3.4.0-030400-generic #201205210521 SMP Mon May 21 09:22:02 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux.
 
Unfortunately, it took several tries to reboot. I kept getting that little page whereon it offers to start up in recovery mode.  Being unadventurous and hammer-headed, I refused to let run through the safe mode. This proved to be a mistake. On one occasion, it ran some kind of listing for hours until I did a hard reset.  After that reset, I chose to have it boot in safe mode. It ran through several items, none of which I can now recall, and then gave me a page where it said something about rebooting in normal mode. It notified me that the graphic drivers would require a hard reset and if nothing happened after I clicked on the Okay button, I should do a hard reset-- or words to that effect. 
 
I clicked on the Okay button and it came right up, asking me for my password. I typed in my password and here I am, fat dumb and fearful.  I should have let it try to restart in protected mode the first time I rebooted the machine. I still do not know if it will reboot smoothly. I will now try it and return to this forum, if I can, and post the results of my next experiment with Precise Pangolin.
That is very odd. I'm sorry you are having such a hard time. I am using kernel 3.4.0 myself on my new Gazelle Professional, and it seems to work fine. I certainly haven't experienced anything like what you are describing.

If the situation doesn't improve, bring up GRUB menu the next time you boot (by holding in the shift key) and choose an earlier kernel. Then, uninstall 3.4.0 by running
```
sudo dpkg -r linux-headers-3.4*
sudo dpkg -r linux-image-3.4*
```Then run
```
sudo update-grub
```and you should at least be back where you were before.

---

### Post by Billy Greenacre on 2012-07-01
Okay. An attempt to put the machine in suspend mode did not work the first time, but it did work the second time.  I will use the suspend mode instead of shutting the machine down until a working kernel becomes available. 

> **Carborundum said:**
> For what it's worth, people are reporting that the current proposed kernel (3.2.0-27.42) fixes the problem. It should go live in a matter of days, assuming nothing untoward happens.
 
Okay, I will be patient, but only because I must.  Which brings to mind yet another worry that I had not thought of until now. What happens when the next update hits the severs? Will installing it overwrite my current kernel with an earlier version? So far, I have been looking at the list of stuff *software update* wants to add and delete, but not messing with it.  Should I tell it not to overwrite the kernel (3.4.0) I now have installed?

---

### Post by Billy Greenacre on 2012-07-01
> **Carborundum said:**
> That is very odd. I'm sorry you are having such a hard time. I am using kernel 3.4.0 myself on my new Gazelle Professional, and it seems to work fine. I certainly haven't experienced anything like what you are describing.

If the situation doesn't improve, bring up GRUB menu the next time you boot (by holding in the shift key) and choose an earlier kernel. Then, uninstall 3.4.0 by running
```
sudo dpkg -r linux-headers-3.4*
sudo dpkg -r linux-image-3.4*
```Then run
```
sudo update-grub
```and you should at least be back where you were before.
  
Thanks for the tip. I will write your code down and then use it if I must. For now, I think that I will stick to suspending the machine instead of shutting it down. I very much prefer a kernel that boots with difficulty and will not freeze, to one that boots smoothly but  freezes at random.
 
BTW, I still do not know if this kernel fixes the random freeze problem. Only further use will tell me if it does. So far, so good.

Thanks,
 
Billy Greenacre

---

### Post by Carborundum on 2012-07-01
> **Billy Greenacre said:**
> 
Okay, I will be patient, but only because I must.  Which brings to mind yet another worry that I had not thought of until now. What happens when the next update hits the severs? Will installing it overwrite my current kernel with an earlier version? So far, I have been looking at the list of stuff *software update* wants to add and delete, but not messing with it.  Should I tell it not to overwrite the kernel (3.4.0) I now have installed?
Whichever kernel you are using now will not be overwritten when the new kernel goes online. You have several kernels installed on your system right now, and GRUB automatically chooses the one with the highest version number.

If you wish to stop using kernel 3.4.0, you must either uninstall it, or manually tell GRUB to boot another one.

---

### Post by isantop on 2012-07-02
> **Billy Greenacre said:**
> Wayul,  shuckins! Canonical came out with an update today. I let it install itself on my system. Guess what? Not only is the kernel still 3.2.0-26-generic #41, it made matters much worse! I can't stay online nearly as long as I could before the current update.  The system freezes shortly after I get online, every time. I'll be lucky to finish this message without a system freeze. 
 
I will give your suggestion a try, but I really think that Canonical should be a bit more responsive to these kinds of situations.  If they have a fix for the problem, why haven't they made it a part of the normal update?  I guarantee you that *Apple* would have already posted a fix as well as putting it in the update pipe.

The update is getting ready to go through quality assurance to ensure that it won't cause any problems for people on other hardware. Every software company will have pretty strict QA procedures that may take a while to get through, and the problem is double with open source companies, where any number of changes *may* have made it into the update. It's also halved with Apple, since they only have to test updates on a very limited set of hardware.

---

### Post by Billy Greenacre on 2012-07-03
I want to offer my sincere thanks to you and everyone else on this board for being so much help. Since I upgraded to the 3.4.0 headers and image, I have been running four things at the time: Firefox playing Flash files on YouTube, Blender with a near one-half gig file running, Gimp with a 500 megabyte jpg and LIbreOffice with my manuscripts. 
 
I have been running with this load for nearly two days now and no, I repeat, **no** freezes of* any kind*. As far as I am concerned, *this* system with *this* particular hardware is running at full capacity.  Now all I have left is a piddling little issue with Firefox and the way it is wont to handle bookmarks.  Whatever that is, I am certain that I need to take it up on a Firefox forum.
 
Again, many thanks Carborundum and System76 and all other that have helped me here.
 
Billy Greenacre.

---

### Post by jiena on 2012-07-25
Thank God we have Ubuntu Forums. I should log in more often I suppose!
The first time I saw "System program problem detected" I pressed the report button and got suspicious when it asked me for my password.  I chose not to report the problem because I thought it might be a keylogger. So I simply ignored it; after all, my computer is working without any problems.  
Is there any way I can be sure that messages like this are legit?  
Do I need to be cautious if similar boxes pop up on the screen?

---

### Post by isantop on 2012-07-26
> **jiena said:**
> Thank God we have Ubuntu Forums. I should log in more often I suppose!
The first time I saw "System program problem detected" I pressed the report button and got suspicious when it asked me for my password.  I chose not to report the problem because I thought it might be a keylogger. So I simply ignored it; after all, my computer is working without any problems.  
Is there any way I can be sure that messages like this are legit?  
Do I need to be cautious if similar boxes pop up on the screen?

You don't need to worry about this. This is perfectly normal, and not a keylogger. It needs your password because some of the system log files are not system-readable, and it needs root access to get information about the system (like the vendor name, model number, etc.).

The password window will list what is trying to gain privileges. If that isn't something you recognize or initiate, then you should refrain. But the fact is that there simply isn't really any malware for Ubuntu. And, in order for any to be installed, you would need to type your password in to install it. Basically, if it asks you for your password after you initiated something, then it will usually be perfectly safe. 

Also keep in mind that the app requesting the password will never actually see the password you type in.

---

### Post by tliketea on 2012-08-03
> **isantop said:**
> 
The password window will list what is trying to gain privileges. If that isn't something you recognize or initiate, then you should refrain. 


It list as much information as the initial dialog gives, none ([see here]("http://askubuntu.com/questions/43103/system-always-start-with-system-program-problem-detected-dialog"))! That's why I, too, have been insecure about it and chose to not enter my password (bad if your OS makes you feel that way) ... 

> **isantop said:**
> 
But the fact is that there simply isn't really any malware for Ubuntu.


No malware, you know of, doesn't mean no malware.  And there **will be** a first time once. Making assumptions like this will not help then.

> **isantop said:**
> 
 And, in order for any to be installed, you would need to type your  password in to install it.
 

... like the window that pops up after a "system program problem detected" message?!

I hate being negative, but I feel like since I am aboard the Ubuntu train (6.04) Precise Pangolin is the least stable version I've ever used. 

Furthermore I am using Ubuntu as my production system and have spend many hours fixing smaller and bigger issues since the 12.04 installation ... This is just one more issue in a long row :(

However ... no hard feelings -- no one is forced to use it.
-T

---

### Post by isantop on 2012-08-03
> **tliketea said:**
> It list as much information as the initial dialog gives, none ([see here]("http://askubuntu.com/questions/43103/system-always-start-with-system-program-problem-detected-dialog"))! That's why I, too, have been insecure about it and chose to not enter my password (bad if your OS makes you feel that way) ... 



No malware, you know of, doesn't mean no malware.  And there **will be** a first time once. Making assumptions like this will not help then.



... like the window that pops up after a "system program problem detected" message?!

I hate being negative, but I feel like since I am aboard the Ubuntu train (6.04) Precise Pangolin is the least stable version I've ever used. 

Furthermore I am using Ubuntu as my production system and have spend many hours fixing smaller and bigger issues since the 12.04 installation ... This is just one more issue in a long row :(

However ... no hard feelings -- no one is forced to use it.
-T

Right, but there's no possible way for a piece of malware to take advantage of the system like this. In fact, the rules that allow that password dialog to work will only work if the rule has been installed, which requires root in the first place.

Trust me, Ubuntu is extremely secure. Part of the reason why is because of a lack of interest, but people would be trying now if not for its inherently secure design. It's not easy to compromise.

---

### Post by venik212 on 2012-08-11
No need for viruses-- we get random (and FREQUENT!) "Sorry, a system error has occurred", etc.  With security like that, who needs viruses?

---

### Post by isantop on 2012-08-13
> **venik212 said:**
> No need for viruses-- we get random (and FREQUENT!) "Sorry, a system error has occurred", etc.  With security like that, who needs viruses?

Again, this is not a security hole. This has nothing to do with malware or viruses. 

This thread seems to be spreading misinformation. I'm going to close it.

---

