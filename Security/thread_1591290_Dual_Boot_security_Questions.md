---
title: "Dual Boot security Questions"
date: 2010-10-09
forum: Security
---

### Post by rCiv on 2010-10-09
Good evening lurkers,

As I further my understanding of basic security concepts I am contemplating loading a spare 50gb partition made at Ubuntu install with a windows xp copy which I have paid for (unfortunately) because A: I paid for it, and B: I like to game from time to time and C: Having a live M$ environment to work with on my network should I decide to adventure deeper into the annals of information security.

Now because I need to use my graphics card to the max because I paid extra for quality hardware, I feel I cant game in "medium" modes on Wine or Cedega.

So, my concern at this point, is obviously, if my winblows partition is compromised, my Linux partition will be at risk as well should a potential intruder be savvy enough to see what is living next door on the hard drive, so I'm wondering if I encrypt my entire Ubuntu file system (swap, /home, and /) prior to loading the windows partition, and then obviously securing the windows partition while offline with pre-downloaded executables from Ubuntu, will I still be in danger of data manipulation on my Ubuntu partitions? (I'm only concerned with manipulation because if someone wipes my drive because they can't access the encrypted data on the other partitions as a result of gaining admin privileges in windows, they still don't technically gain access to my Linux files and I can just reinstall a fresh copy whilst wiping windows and its a stalemate, sort of)...

Keep in mind that, while online with XP I will only browse with firefox configured as per my Ubuntu guidelines, use Zone Alarms free-ware firewall and white-list, ONLY play games, so no Outlook/IE etc...
And I will also still be behind my Router/NAT Firewall. 

On the plus side the one advantage I can see from here so far is being able to mount my windows partition from Ubuntu and scanning it which I feel will be MUCH more effective then virus scanning/forensics inside XP.

/Discuss

---

### Post by rCiv on 2010-10-09
Added note: I only play legal copies of games, so no keygens/patches and other silliness to worry about.

(Yes, I actualy care about paying for great software/games and feeding developers and plan to donate to the Ubuntu project very shortly for providing such AMAZING free software  and knowledge).

(Is it possible to donate I wonder? Let me check the website, lol, its at LEAST worth what i paid for windows...)

---

### Post by HPD2 on 2010-10-09
Your Ubuntu Partition would be mostly safe if the windows install was some how compromised.  About the worst that could happen from running windows (assuming ext4 file system) is the drive could be formated.  Windows XP, Vista, and 7 do not have support for the ext4 file system.  However if you maintain security updates, a basic firewall, virus scanner, and practice safe browsing, you shouldn't run into many issues.

---

### Post by Velnias on 2010-10-09
If I understood correctly, Windows fully satisfies your needs. Use Avast with scanning on boot.
So why you need Ubuntu?

---

### Post by OpSecShellshock on 2010-10-09
Best thing to do would probably be to use the Windows installation for gaming only, and do all other stuff with Ubuntu. Well, that's strict, but you know--Windows-only stuff. There's less and less of that all the time.

Leave the Ubuntu partition formatted in ext4, and I suppose the Windows partition as NTFS, and don't share any data between them. That's easy enough since Windows can't do anything with the ext4 drive except know there's something there. Don't be alarmed when you can't change permissions to files on the NTFS partition from an Ubuntu session--that's normal.

From a risk management perspective, there's nothing the Windows partition can do to hurt the Ubuntu build. The threat models for the two operating systems are completely different.

---

### Post by rCiv on 2010-10-09
> **Velnias said:**
> If I understood correctly, Windows fully satisfies your needs. Use Avast with scanning on boot.
So why you need Ubuntu?

It doesn't, I don't remember saying that anywhere, it only satisfies my  sporadic gaming needs, and none of the others(just to name a few) such as my interest in Linux and the Linux/open source community, network/information security, safe handling of my personal day to day information,, and finally it definitely does not fulfill my need to learn and progress as a security enthusiast.

 Almost everything on Linux and Linux knowledge bases/communities directly encourage the personal growth of it users and molds them into highly advanced users by traditional standards with understanding of advanced security concepts, windows does not satisfy my need to be part of such a globally connected and united community. 

I love Ubuntu and everything about it, that is why I need Ubuntu... and i wouldn't bother Dual booting if i just wanted to hang out in windows all day and wait for security patches.

---

### Post by rCiv on 2010-10-09
> **HPD2 said:**
> Your Ubuntu Partition would be mostly safe if the windows install was some how compromised.  About the worst that could happen from running windows (assuming ext4 file system) is the drive could be formated.  Windows XP, Vista, and 7 do not have support for the ext4 file system.  However if you maintain security updates, a basic firewall, virus scanner, and practice safe browsing, you shouldn't run into many issues.

Perfect! Thank you, very useful info! 

Yes I will obviously only game with it and not run anything else.. . and only browse Unbuntu forums / trusted game forums etc... like I said I only need it to boot into sometimes when i feel like playing a few games, which I usualy play for a few hours at a time, so the extra 2 minutes it takes to boot into another system if far outweighed by the time savings I get from not having to endlessly configure Wine or Cedega every time I want to try a new game and also avoiding the graphics quality issues is a big plus... 

Also from a forensics point of view its a big plus I believe to be able to scan from outside of windows (live CD or simply dual boot) am I wrong?

---

### Post by rCiv on 2010-10-09
> **OpSecShellshock said:**
> Best thing to do would probably be to use the Windows installation for gaming only, and do all other stuff with Ubuntu. Well, that's strict, but you know--Windows-only stuff. There's less and less of that all the time.

Leave the Ubuntu partition formatted in ext4, and I suppose the Windows partition as NTFS, and don't share any data between them. That's easy enough since Windows can't do anything with the ext4 drive except know there's something there. Don't be alarmed when you can't change permissions to files on the NTFS partition from an Ubuntu session--that's normal.

From a risk management perspective, there's nothing the Windows partition can do to hurt the Ubuntu build. The threat models for the two operating systems are completely different.

Again thank you!

---

### Post by Velnias on 2010-10-10
I see. So you should cut off Windows from internet and - Voila! - you using Ubuntu and no security breaches in Windows ( and without wasting time and resources on naive "layered security", without Windows updates, firewall, antivirus, antimalware, sandbox, HIPS... ).
 Its that simple.

---

### Post by rCiv on 2010-10-10
> **Velnias said:**
> I see. So you should cut off Windows from internet and - Voila! - you using Ubuntu and no security breaches in Windows ( and without wasting time and resources on naive "layered security", without Windows updates, firewall, antivirus, antimalware, sandbox, HIPS... ).
 Its that simple.

Unfortunately I play networked games, but I think with a firewall, security updates, and no IE/Email, I should be fine. The main issue I was worried about is if the Linux files would be vulnerable should someone compromise the windows partition, I just didn't want all my eggs to be in the windows basket. I'm fine with the slight possibility someone compromises my dummy windows part as they wont be able to manipulate files on the Ubuntu side and I will be in a great position to monitor the Windows side from Ubuntu with the array of available security tools at my disposal.

---

### Post by teejaybee on 2010-10-11
Do you need to keep your current Ubuntu install? Could you format and reinstall it? If so, use the alternate CD and set up your main and swap partitions as encrypted with dmcrypt etc. Windows won't be able to read or do anything to the partitions except maybe delete them. Your only problem would be /boot - leave it unencrypted for ease of use but then windows could potentially replace a kernel or something - would be a targeted attack anyway. You can avoid that but it makes things a little more cumbersome - you boot from a USB drive that contains your /boot stuff.

I just did it yesterday on an eeepc laptop dual booting win7 and it works like a charm. My main reasoning was if I lose the laptop or it gets stolen, they've got the hardware but can't effect me in any other way via access to my private information.

---

### Post by rCiv on 2010-10-11
> **teejaybee said:**
> Do you need to keep your current Ubuntu install? Could you format and reinstall it? If so, use the alternate CD and set up your main and swap partitions as encrypted with dmcrypt etc. Windows won't be able to read or do anything to the partitions except maybe delete them. Your only problem would be /boot - leave it unencrypted for ease of use but then windows could potentially replace a kernel or something - would be a targeted attack anyway. You can avoid that but it makes things a little more cumbersome - you boot from a USB drive that contains your /boot stuff.

I just did it yesterday on an eeepc laptop dual booting win7 and it works like a charm. My main reasoning was if I lose the laptop or it gets stolen, they've got the hardware but can't effect me in any other way via access to my private information.

That actualy sounds like a great idea, I will try that, but maybe you could clarify something,  if /boot is EXT4 and on the internal HD, would windows still be able to manipulate it? Its my understanding that windows has no support for ext4 file system.

Let me know, thanks!

---

### Post by teejaybee on 2010-10-12
That's why I said it would have to be a targeted attack on you - i'm sure there's a way for windows to talk ext4 somewhere / somehow by someone, but whether it's mainstream and whether you'll ever have anything like that leveled against your machine as a payload from something nasty i'm not sure. I'm not sure if a linux kernel fired up in a virtual machine on a windows machine can natively talk to other partitions, but that could be a vector. Once again, whether that type of thing, if possible, would ever be used in the huge worm/botnet/mass-email attacks I don't know, as it would probably require quite a bit of data/code to do that.

For occasional use, i'm happy to use my locked-down minimal win7 install on said laptop, and i'm pretty paranoid when it comes to security. Firefox+noscript, DEP, antivirus, always updated, behind NAT, etc should be bare minimum for your windows gear.

---

### Post by wacky_sung on 2010-10-12
Personally i do not trust window as much often people complain about issue with virus / adware and they blame Linux being weak in which they never realise they dual boot linux with window.Very much most of the time,the issue arises from window OS itself.

---

