---
title: "A VERY PAINFUL DAY...10 Years of memories..."
date: 2010-06-11
forum: Testimonials &amp; Experiences
---

### Post by btbluesky on 2010-06-11
I just want to post this from my heart and not really care if anyone read it. 

Today is a very painful day for me, because after 10 years of using Linux, I finally have to switch back to Windows. As a married programmer, I believe I'm not a novice in the *nix land, and this is very emotional for me.

Remembering back in Redhat 5, I got my first copy. Edit the fstab, x11.cfg, learn the vi jedi ways. Then got to Mandriva, easier, prettier. Then I got serious, dive right into gentoo, and other source based distro. compile your own kernel, check your gcc flags. Things that make zero sense to other people, make decent sense to me thanks to my CS compiler class. From seeing how the Filesystem works, to writing a full blown set of custom backup bash scripts, I have been blessed to be able to learn all that, which also enable me to perform my duty at work more efficiently. 

We cannot undermine the contributions RHAT gave to the community, but Ubuntu has been instrumental for alot Linux exposure in these couple years. Like Apple have long discovered, the key to a great platform is general users acceptance, which has the 1st rules of being user friendly. No amount of technical hacks would make your platform famous, unless a high pool of users are using it. Ubuntu has been aiming to achieve that in desktop space, and it's been great. Still it's not enough, and time is running out. My situation is not unique, and I'm sure there are tons of users have similar experience. Here is my sad states:

- I'm an audiophile, I love highend sound. 300B tube amp with a high eff spks I can listen all day. And been fighting the ALSA+pluseaudio for like the last 2 years. I removed it, defeat the dmix, and by the time I got around to get the flash to play sound directly to ALSA, it's the 6 mo upgrade time, and I have to do it all over again.

- Got the good 802.11n adapter, doesn't work. Check the forum, there are ways....but come on. Been fighting the same battle for 10 yrs.

- Every 6 mo, the upgrade make the system much slower. Been just backup the etc and home dir, do a fresh install, and then put back the setting I want manually. But gee, thats 2 weekends thats gone. As more settings I have to do, there are just no way I can keep tracks of all these.

- When I reboot back into the new Win 7 install, boot time is much faster. I admin ubuntu been doing a great job. But still, it's painful to see MSFT got us on this. 5 yrs back, it wouldn't be possible. now the linux got more bloat as more drivers/plugs needs to boot, its just painful to see.

- VMWARE....or any virtualization. company uses it. I have it in my laptop. I can just run ubuntu in it, still get all the good stuff whenever I want.

   I admit partly it's because people like me get more busier and more responsibilities as we aged, and cannot hack the etc dir until dawn anymore like when you're in your 20s. But in general, it's painful to have to fight the same battles for so long. 10 years ago, I'm stuggling with the device/sound drivers, the settings, the desktop effects, today its the same, except its much more complicated. Gnome and KDE are both GUILTY in this regard (well, gnome is less...) in feature creeps, without making sure the older features are working perfectly. Not to mention all the device makers are still treating us like dirts, not giving us access to their docs. All these are just too much when you have a family, a job, and millions of other things/projects you need to work on.

   I'll always make space for an installation, but as the primary OS, I just cannot keep fight the battle no more. I have in my linux vmware OSX, solaris (yet..I know...), winxp, win7. Now I have to convert all the ext4 space (all 6 TB of them) into ntfs/vfat, and do everything all over again.

   Still, keep fight the battle guys. Long live the penguin.....:guitar:

---

### Post by Linuxforall on 2010-06-11
When you mention that boot time is faster in Win7, your credibility is totally lost there, even my die hard Windows fan friends openly admit that in boot and shutdown, Lucid has Win7 licked.

---

### Post by marshmallow1304 on 2010-06-11
From the problems you listed, it sounds to me like you might be more comfortable with Debian.

But I am interested as to why you didn't use a separate partition for /home.


In any case, good luck. ):P

---

### Post by btbluesky on 2010-06-12
> **Linuxforall said:**
> When you mention that boot time is faster in Win7, your credibility is totally lost there, even my die hard Windows fan friends openly admit that in boot and shutdown, Lucid has Win7 licked.

Yes...on fresh install. I did an upgrade coz I have no weekends to spare the past couple months. And it slows to a crawl. I have both KDE and gNome install (coz I use some kde apps sometimes), and 6 hdds, (like 7-8 tb), so even with lucid new no-fsck boot, it's slower, in my quad intel 9200 OCed to 3.8Gz w/ 6Gb ram.

---

### Post by btbluesky on 2010-06-12
> **marshmallow1304 said:**
> From the problems you listed, it sounds to me like you might be more comfortable with Debian.

But I am interested as to why you didn't use a separate partition for /home.


In any case, good luck. ):P

I have a seperate home. A seperate home doesn't help in anyway, coz you want to clear all the old settings in your .gnome, .sound , .wutever when you do fresh install. god knows what flags Gnome/kde decided to changed, and the old ones would store in your home. Or do upgrade and risk old setting slowing things down.

I understand when you have 6 months to roll a new OS, there wouldn't be enough manpower/time to do full(...or any) regression installation/upgrade testing, it's just life. And its upstream's fault as well (pulseaudio...) alot of time. But having fresh install every couple months, or risk having your daily env slow down. What can I say...

Debian would be a good choice, because it doesn't get update as often (or at all :) ). But as I see it, if we're fighting the battle, might as well use wutever ammo we can get, including experimental ones every 6 mos.

Guess I'm just getting old, going to the dark side with my virtual env would be enough for me at this point.

---

### Post by Riffer on 2010-06-12
Don't know why pulse is such a bear for you, its been great for me.  It could just be your card.

This point confuses me.  If you been using Linux for 10 years and you know that your network card doesn't work, why do you still use it?  A good card that plays nice with Linux is less then $40.  From the specs you gave us it sounds like you have a fairly expensive and new machine, surly you can afford a new card.

Also what version of Ubuntu are you using?  If you are using 64 bit, its a big buggy compared to 32 bit.  I had problems with both sound and network with 64, all was ironed out with 32.

My boot times are 25 seconds with login in screen.  To take much longer then that points to a problem, have you checked your logs?

Lastly I know the standard 32 bit system can only use something like 3.5 gigs of RAM.  With your system you might be better of using the server edition and build your desktop.

And more lastly's, setting up a separate /home partition is fairly easy.  There's very good HOWTO's on the net.  As well there are a few good simple backup apps that you can use.

But whatever you decide, Windows is a good OS.

PS.  I'm 53 and I regularly bork my system, its how I learn.  It takes me about 2 hours to do a fresh install and I can do whatever tweaks from there.  Even with the problems you've mentioned I can't see it taking 2 weekends to be up and running again, with your system more or less the way you want it.

---

### Post by mmix on 2010-06-12
problem is not os, but,

compiler, assembler, cryptic-hardware.

---

### Post by btbluesky on 2010-06-12
> **Riffer said:**
> Don't know why pulse is such a bear for you, its been great for me.  It could just be your card.

This point confuses me.  If you been using Linux for 10 years and you know that your network card doesn't work, why do you still use it?  A good card that plays nice with Linux is less then $40.  From the specs you gave us it sounds like you have a fairly expensive and new machine, surly you can afford a new card.

There is no card. I use a USB dedicated DAC. Pulseaudio by nature have to do conversion (it collects all the streams), which is a no-no if you want pure digital out. I admit this is not for everybody, but I have 6k+ audio equips, so that's my big req. In windows there are 2 options for direct kernel stream to hardware, WASAPI and ASIO. Linux you dun need because ALSA does that, but w/ all the crap on top of it, its just tough.

I moved, new place my cable Internet is really good, 30m downstream. But the modem is in another room. So I need a mimo dual freq receive 802.11n to match the speed. The G wifi is too slow for the connection (I get 10m in G downstream, like 1/3 of what it could be). If you show me a USB 802.11n MIMO 2.4+5gz adapter that works in lucid, I'd get it. There isn't.

> Also what version of Ubuntu are you using?  If you are using 64 bit, its a big buggy compared to 32 bit.  I had problems with both sound and network with 64, all was ironed out with 32.

Again, I run alot of envs, I need the rams. So 32 is out of question.

> My boot times are 25 seconds with login in screen.  To take much longer then that points to a problem, have you checked your logs?


Lastly I know the standard 32 bit system can only use something like 3.5 gigs of RAM.  With your system you might be better of using the server edition and build your desktop.

My work laptop w/ intel SSD + win7 that support TRIM instructions boots in <10. Until they have TRIM in the kernel, we cannot use SSD safely. 

The win7-64 in this home tower that I rarely use, it boots in <14 secs. Of course the 2 "upgrades" (jaunty->karmic->lucid) have lots of residual configs and slow stuff down, but thats the point I made, can't take it.

 I use standard 64 desktop ed with like hundreds more of the apt packages because I need all these desktop apps. the only diff server vs desktop is that you pick your packages, everything else is same. Yah if I have the time fresh install every 6 mos, no problem.

> And more lastly's, setting up a separate /home partition is fairly easy.  There's very good HOWTO's on the net.  As well there are a few good simple backup apps that you can use.

...I have seperate home, read previous post.

> But whatever you decide, Windows is a good OS.

No its not, but at this point, low maintenance to free up my time is good.

> PS.  I'm 53 and I regularly bork my system, its how I learn.  It takes me about 2 hours to do a fresh install and I can do whatever tweaks from there.  Even with the problems you've mentioned I can't see it taking 2 weekends to be up and running again, with your system more or less the way you want it.

That's great man. I wish I can do that until that age. I agree. Maybe it's just me wanting to have everything in exact way I want it that takes time. Thing is after having to write ksh scripts, config servers at work, I gotta do the same thing to get the primary system at home to do want I need is just...I'd con't to use linux, running it in virtual machines for sure. 

cheers

---

### Post by prodigy_ on 2010-06-12
> **Linuxforall said:**
> When you mention that boot time is faster in Win7, your credibility is totally lost there, even my die hard Windows fan friends openly admit that in boot and shutdown, Lucid has Win7 licked.
Not on all hardware. For me Lucid boots fast in a VMWare VM (almost instantly if I disable Plymouth) but it's horribly slow on my bare hardware.

What am I doing wrong?

> **Riffer said:**
> Also what version of Ubuntu are you using?  If you are using 64 bit, its a big buggy compared to 32 bit.  I had problems with both sound and network with 64, all was ironed out with 32.
Now that's an understatement. It's buggy as hell. I haven't really tested 32-bit version but 64-bit Lucid is basically a beta-quality release.

---

### Post by Linuxforall on 2010-06-12
> **prodigy_ said:**
> Not on all hardware. For me Lucid boots fast in a VMWare VM (almost instantly if I disable Plymouth) but it's horribly slow on my bare hardware.

What am I doing wrong?


Now that's an understatement. It's buggy as hell. I haven't really tested 32-bit version but 64-bit Lucid is basically a beta-quality release.

On majority of PC and laptops of variety here, Lucid boots faster compared to Win7 and shuts down even quicker. If Lucid is beta quality release, Windows has always been alpha and SP just made them beta at the owner's expense.

---

### Post by maxideci on 2010-06-13
I sympathize with btbluesky, and agree with him. I am a big fan of linux especially ubuntu, for reasons as working with linux gives me satisfaction. 
I believe MS got it right with Win 7, it really boots very fast, cant say the same for lucid on my machine. I also like btbluesky did the upgrade, instead of fresh install, and I wouldn't term 'lucid boot' as a fast boot. I'm not so busy as to mind waiting bit longer for my machine to boot, hence its not a big issue for me.

After upgrading to Lucid, I ran into many issues, some of them are yet to be solved and I almost gave up, cause, I have spent lot of time finding solution, every now and then I try to fix old problems, but in vain.

I was at LinuxTag and attended talk "Making Linux Sexy: Don't Forget the End User by Matt Asay (Canonical), Ivanka Majic (Ubuntu)" there were 2 main focal points, 1) to address end user as user and 2) to make that one killer application which brings people to ubuntu/linux, and iPhone example was made. Well I think, we dont need killer application, linux success stories are enough for people to switch. Ubuntu fan base is enough evidence of how popular it is. Nothing was said about people who were frustrated or not happy with ubuntu and switching to other distros.

**These are the issues still bother me, and they never appeared in karmic**
[LIST=1]
[*]WARNING: The following packages cannot be authenticated!
[*]Bluez daemon is not running, blueman-manager cannot continue.
[*]Your battery may be broken...48.2%....
[*]Huawei_E1750 Mobile broadband keeps getting disconnected, and reconnecting it is a long process sometimes.
[/LIST]

We got to make our side of grass greener. Sorry, I'm not ranting here, nor I will purge linux and live on Windows...

> **btbluesky said:**
> I just want to post this from my heart and not really care if anyone read it. 

Today is a very painful day for me, because after 10 years of using Linux, I finally have to switch back to Windows. As a married programmer, I believe I'm not a novice in the *nix land, and this is very emotional for me.

Remembering back in Redhat 5, I got my first copy. Edit the fstab, x11.cfg, learn the vi jedi ways. Then got to Mandriva, easier, prettier. Then I got serious, dive right into gentoo, and other source based distro. compile your own kernel, check your gcc flags. Things that make zero sense to other people, make decent sense to me thanks to my CS compiler class. From seeing how the Filesystem works, to writing a full blown set of custom backup bash scripts, I have been blessed to be able to learn all that, which also enable me to perform my duty at work more efficiently. 

We cannot undermine the contributions RHAT gave to the community, but Ubuntu has been instrumental for alot Linux exposure in these couple years. Like Apple have long discovered, the key to a great platform is general users acceptance, which has the 1st rules of being user friendly. No amount of technical hacks would make your platform famous, unless a high pool of users are using it. Ubuntu has been aiming to achieve that in desktop space, and it's been great. Still it's not enough, and time is running out. My situation is not unique, and I'm sure there are tons of users have similar experience. Here is my sad states:

- I'm an audiophile, I love highend sound. 300B tube amp with a high eff spks I can listen all day. And been fighting the ALSA+pluseaudio for like the last 2 years. I removed it, defeat the dmix, and by the time I got around to get the flash to play sound directly to ALSA, it's the 6 mo upgrade time, and I have to do it all over again.

- Got the good 802.11n adapter, doesn't work. Check the forum, there are ways....but come on. Been fighting the same battle for 10 yrs.

- Every 6 mo, the upgrade make the system much slower. Been just backup the etc and home dir, do a fresh install, and then put back the setting I want manually. But gee, thats 2 weekends thats gone. As more settings I have to do, there are just no way I can keep tracks of all these.

- When I reboot back into the new Win 7 install, boot time is much faster. I admin ubuntu been doing a great job. But still, it's painful to see MSFT got us on this. 5 yrs back, it wouldn't be possible. now the linux got more bloat as more drivers/plugs needs to boot, its just painful to see.

- VMWARE....or any virtualization. company uses it. I have it in my laptop. I can just run ubuntu in it, still get all the good stuff whenever I want.

   I admit partly it's because people like me get more busier and more responsibilities as we aged, and cannot hack the etc dir until dawn anymore like when you're in your 20s. But in general, it's painful to have to fight the same battles for so long. 10 years ago, I'm stuggling with the device/sound drivers, the settings, the desktop effects, today its the same, except its much more complicated. Gnome and KDE are both GUILTY in this regard (well, gnome is less...) in feature creeps, without making sure the older features are working perfectly. Not to mention all the device makers are still treating us like dirts, not giving us access to their docs. All these are just too much when you have a family, a job, and millions of other things/projects you need to work on.

   I'll always make space for an installation, but as the primary OS, I just cannot keep fight the battle no more. I have in my linux vmware OSX, solaris (yet..I know...), winxp, win7. Now I have to convert all the ext4 space (all 6 TB of them) into ntfs/vfat, and do everything all over again.

   Still, keep fight the battle guys. Long live the penguin.....:guitar:

---

### Post by btbluesky on 2010-06-14
Thanks maxideci. you bring up the main point. Like I said, we cannot expect full blown regression test when u have 6 months to deliver a new OS. Still the changes in new versions have to be **incremental, modular with extensive unit testing, and ... doesn't break the old setup/config/features.**

Why do I have to defeat dmix and pulseaudio every 6 months manually?! I choose not to use this feature, and get jammed in my throat every 6 months. And believe me every time the hack to do it is different.

I absolutely love having new features to play with, but they have to admit that asking users to reinstall every 6 mos or risk slow/broken system is not realistic.

Maybe the solution is to have a main tool (like the KDE system tool, but more extensive) that can manipulate the /etc and all the other device/system setting, even some big app's setting as well. And responsible to purging any unless, incompatible custom/old setting in /etc or anywhere.

---

### Post by ukripper on 2010-06-15
> **prodigy_ said:**
> Not on all hardware. For me Lucid boots fast in a VMWare VM (almost instantly if I disable Plymouth) but it's horribly slow on my bare hardware.

What am I doing wrong?


open ```
sudo gedit /etc/initramfs-tools/conf.d/splash
```
and see if FRAMEBUFFER=y then mark it as "n" > FRAMEBUFFER=n
save and exit.
then update 
```
sudo update-initramfs -u
```
It should be quicker now when you reboot.

---

### Post by maxideci on 2010-06-15
I do not see any file called splash in /etc/initrmfs-tools/conf.d/. All I have is a file called "resume" with one single line of text 'RESUME=UUID=44534a8d-68eb-4687-8c82-cba5a58830da'.

> **ukripper said:**
> open ```
sudo gedit /etc/initramfs-tools/conf.d/splash
```
and see if FRAMEBUFFER=y then mark it as "n" 
save and exit.
then update 
```
sudo update-initramfs -u
```
It should be quicker now when you reboot.

---

### Post by WinterRain on 2010-06-15
> **btbluesky said:**
> 

I absolutely love having new features to play with, but they have to admit that asking users to reinstall every 6 mos or risk slow/broken system is not realistic.



Who says you have to reinstall every 6 months to get new apps and features? That's what ppa's are for. Jaunty and karmic users can use the same apps as lucid users.

---

### Post by tkoco on 2010-06-16
> **maxideci said:**
> I do not see any file called splash in /etc/initrmfs-tools/conf.d/. All I have is a file called "resume" with one single line of text 'RESUME=UUID=44534a8d-68eb-4687-8c82-cba5a58830da'.

Like you, I found the mentioned file to be absent. So I created it and added the FRAMEBUFFER=n to the file. After saving and updating, I rebooted. ukripper is correct. The boot up is faster.

---

### Post by mastablasta on 2010-06-16
Why upgrades are necessary every 6 months if you know that it will take time to make it all as you want it? why not just use LTS and upgrade every 3 years? It would have saved you a lot of time.
 
Also i use KDE applications in Gnome. ups, i guess i am still learning. I dint' know you need to have full KDE installed to do that.

---

### Post by ikeurb on 2010-06-16
Now I'm depressed. I swithced to Ubuntu for a couple reasons, a project at work, and becuase I couldnt tolerate Windows anylonger. Vista killed what liking I had left for Windows. But, yes I hear that Windows 7 is nice. But not sure I want to shell out the dollars for a new highend laptop that has enough resources to run Win7.
 
I think I will stay with Ubuntu. ;)

---

### Post by irv on 2010-06-16
Your thread caught my eye so I read through it. For the 10 years you say you have dealt with Linux Redhat, Ubuntu, etc, I don't see much input on this forum. I just found three thread this being one. I jumped on the Ubuntu bandwagon years ago and am still on it. I do use Win7 on occasion, but for my everyday work and pleasure I use Ubuntu. 
Yes, I am one who chooses to upgrade and update on a regular basis and I know there will be issue to iron out. And this is the case even when I would upgrade to different versions of Windows.
With that said, I find you get out of something what you put into it. I have tried to help other on this forum and in return I have gotten much help out here myself. I am running 10.04 now for about three weeks, and I have everything running exactly as I want it. I am a happy end user. And when I see a thread like this I can't help to think to myself, this fellow or in some cases gal, has not given to the community very much so how can they expect to be happy. If you feel you need to go back to Windows do so, because I feel this community of Ubuntu user will not feel the loss.
You said in your original post “I believe I'm not a novice....” and if so why have you not shared with the community some of your skills (programmer) in order to help other? 
I am sorry if I offended you but this is just my heart's feeling, and we all may feel differently but if you would have gotten involved with all the users out here you would feel much differently about Ubuntu.

---

### Post by mastablasta on 2010-06-17
My bro uses it at work. He has similar problems upon updating. Having to do all the settings that is and to make it all work again. Problem is he is upgrading every once in a while so that he can run certain programs with newer features. So they have to upgrade. He uses WinXP at home and believes it is far better as desktop or at least he is not so impressed with Linux. I talked with him about their servers, but for those he says linux is quite good (especially because it is free). I still think the problem with desktop is that so many support is lacking and so many things can simply not be done.

---

### Post by irv on 2010-06-17
I have Ubuntu Linux running on a server, desktop, and my laptop, and I find it one of the best OS's out here for all three machines. Once you learn your way around in Linux you can fix most anything. Grant you it is not for everyone because I have some friends I would never put Linux on there machines because I would be on the phone all the time trying to help them. And again there are some who would take to it like a duck to water. Different strokes for different folks.

---

### Post by VastOne on 2010-06-17
> **prodigy_ said:**
> Now that's an understatement. It's buggy as hell. I haven't really tested 32-bit version but 64-bit Lucid is basically a beta-quality release.

Do you have any data to back up this statement or is it just your 1 off experiences?  I use 64 bit exclusively in my business, at school, work and at play and am not seeing what you are describing.

---

### Post by etdsbastar on 2010-06-17
> **mastablasta said:**
> Why upgrades are necessary every 6 months if you know that it will take time to make it all as you want it? why not just use LTS and upgrade every 3 years? It would have saved you a lot of time.
 
Also i use KDE applications in Gnome. ups, i guess i am still learning. I dint' know you need to have full KDE installed to do that.

I agree only 50% with you because linux distros are first of all open source secondly they are being developed from various parts of the world by various expert programmers and supporters and In my opinion Ubuntu and its derivatives have got top most position till now as compared to other distros, The major problem is with hackers and crackers, most of the upgrades are from positively from "security side", and hence HARDENING YOUR SYSTEM SECURITY on each and every upgrade. If made upgrades after every 3 years, you all know what happens with our servers and clients... 

So, Believe canonical and always respect all the users and developers who have done such a beautiful and awesome job....

FROM MY SIDE.... HATS OFF AND KEEP UPGRADING ... TO ALL UBUNTU TEAM (INCLUDING USERS)...

---

### Post by Johnsie on 2010-06-18
I agree sound on Linux sucks. Ask any professional sound engineer.

---

### Post by irv on 2010-06-18
> **Johnsie said:**
> I agree sound on Linux sucks. Ask any professional sound engineer.

I can agree and disagree with this statement. First sound itself has short comings, but I control the sound system and do all the recording at the chapel I attend and it works great. I tie into the PA system and record using Audacity, and then upload the MP3 files to a server on the Web, and in about 10 minutes of recording. Works great for this, and by the way I am not a professional sound engineer. In fact, I only have one ear so I do everything is Mono. :lolflag:

---

### Post by C.S.Cameron on 2010-06-18
I enjoy visiting my old home town, it usually takes 4 or 5 days to remember why I left.
Microsoft will always be Microsoft.

---

### Post by ikeurb on 2010-06-21
Sound has been our issue too. We need a sound card, preferred to use external rack mount, but can't find one that works at all with Linux. So we are using an internal PCIe sound card with 8 channels in and 8 channels out. 

We at least got this card to work, but it wasn't easy. Working with ALSA drives isn't the most user friendly thing to do.

---

### Post by ikeurb on 2010-06-29
My laptop dual boots to Ubuntu and Windows Vista. Last night, I upgraded the Vista partition to Windows 7. OMG, it took forever.
 
The compatability check in the Win7 install said I need to "deauthorize iTunes" before It could proceed. So I deauthorized iTunes and restarted Win7 install. Then the compatability check said I needed to unistall iTunes. Are you kidding me? Why couldnt it figure that out in the first place. So, I ininstalled iTunes, and then restarted the Win7 install again.
 
Of course, Win7 install then complained I needed to uninstall an HP application. So, i did that and restarted Win7 install yet again. This went on and on for several different apps, drivers, etc.
 
If anyone is going to update their old Windows to Win7, I recommend they update all drivers first.
 
Finally, I started the actual Win7 install, and it took all night to install it. I went to bed and let it run, copy, install itself why I got some sleep.
 
Long story short, I'm glad Ubuntu installs, updates, and upgrades much easier than Windows. I'm still hating Windows! :biggrin:

---

### Post by etdsbastar on 2010-06-29
> **ikeurb said:**
> My laptop dual boots to Ubuntu and Windows Vista. Last night, I upgraded the Vista partition to Windows 7. OMG, it took forever.
 
The compatability check in the Win7 install said I need to "deauthorize iTunes" before It could proceed. So I deauthorized iTunes and restarted Win7 install. Then the compatability check said I needed to unistall iTunes. Are you kidding me? Why couldnt it figure that out in the first place. So, I ininstalled iTunes, and then restarted the Win7 install again.
 
Of course, Win7 install then complained I needed to uninstall an HP application. So, i did that and restarted Win7 install yet again. This went on and on for several different apps, drivers, etc.
 
If anyone is going to update their old Windows to Win7, I recommend they update all drivers first.
 
Finally, I started the actual Win7 install, and it took all night to install it. I went to bed and let it run, copy, install itself why I got some sleep.
 
Long story short, I'm glad Ubuntu installs, updates, and upgrades much easier than Windows. I'm still hating Windows! :biggrin:

Wow, I even like Ubuntu ... the best ever distro ever i saw, and sorry for the startup word 'Wow' its for Ubuntu and the way of writing you have explained.... its great... i even hate windows.

---

