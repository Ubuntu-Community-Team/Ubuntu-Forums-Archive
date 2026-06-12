---
title: "Ubuntu CE v1.3 released!!"
date: 2006-09-26
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2006-09-26
We have just released Ubuntu Christian Edition v1.3. 

There have been some changes made to the web content filtering. The Firefox proxy settings have been "locked down" to prevent users from bypassing the filtering. You can also now use your Ubuntu CE system as a network proxy/filtering server by setting the other systems proxy settings to the IP address of the Ubuntu CE system and port 8080. An "Access Denied" log has been added to the Dansguardian GUI to allow users to view information on page requests that were denied as a text based or html based document. 

Three new programs have been added to this release. They include [Planner Project Scheduler]("http://www.simpleprojectmanagement.com/planner/"), [Scribus Desktop Publisher]("http://www.scribus.net/"), and [Nvu Web Authoring System]("http://www.nvu.com/index.php"). These can all be very useful for Churches as well as individuals. 

Three games have also been added. They include [Frozen Bubble]("http://www.frozen-bubble.org/"), [Breakout]("http://freshmeat.net/projects/gnome-breakout/"), and [Sudoku]("http://gnome-sudoku.sourceforge.net/"). These were added by user request.

Other changes include the addition of wallpapers provided by [CarriedCross.org]("http://www.carriedcross.org/"), new Usplash and Bootsplash, customized default Firefox homepage and bookmarks, some minor graphical adjustments, and a minor bug fix in the Ubuntu CE Installer.

Check it out on the project site, [ChristianUbuntu.com]("http://www.christianubuntu.com")

God Bless, Jereme

---

### Post by Christian_Joe_Linux on 2006-09-26
I would like to use Christian Linux, but I don't want my Firefox "locked down".  Is it possible for the "administrator" of my Christian system to open up the settings?

---

### Post by bthumper on 2006-09-26
Live CD boots up fine but I am having problems installing. 

I get to the partition part of the installer and when I choose manual partitioning option, it seems to go into a loop and then freezes up.

MD5 checks out ok. Downloaded and burned another CD with same results. Not sure where to go from here. :(

---

### Post by mhancoc7 on 2006-09-26
> **bthumper said:**
> Live CD boots up fine but I am having problems installing. 

I get to the partition part of the installer and when I choose manual partitioning option, it seems to go into a loop and then freezes up.

MD5 checks out ok. Downloaded and burned another CD with same results. Not sure where to go from here. :(

Well, I am not sure what is going on there. I will check it out and see if I can repeat the behavior.

Thanks, Jereme

---

### Post by montgoej on 2006-09-26
Just upgraded to Ubuntu CE v1.3 and everything's running smoothly. I really like the boot splash and Scribus too.
~Jordan Montgomery

---

### Post by mhancoc7 on 2006-09-26
> **Christian_Joe_Linux said:**
> I would like to use Christian Linux, but I don't want my Firefox "locked down".  Is it possible for the "administrator" of my Christian system to open up the settings?

Yes you can make the changes using your root account (sudo). PM me and I will give you instructions.
God Bless, Jereme

---

### Post by mhancoc7 on 2006-09-26
> **bthumper said:**
> Live CD boots up fine but I am having problems installing. 

I get to the partition part of the installer and when I choose manual partitioning option, it seems to go into a loop and then freezes up.

MD5 checks out ok. Downloaded and burned another CD with same results. Not sure where to go from here. :(

I just tested the iso using the Manual Partitioning and it works great. Have you installed Ubuntu CE before? It may be an issue with Ubuntu in general. Jereme

---

### Post by mhancoc7 on 2006-09-26
> **montgoej said:**
> Just upgraded to Ubuntu CE v1.3 and everything's running smoothly. I really like the boot splash and Scribus too.
~Jordan Montgomery

Great! Thanks for letting me know.
God Bless, Jereme

---

### Post by Christian.Sportsman on 2006-09-26
> **mhancoc7 said:**
> 
Other changes include the addition of wallpapers provided by [CarriedCross.org]("http://www.carriedcross.org/")...


Where can the new wallpapers be found?  I looked in /usr/share/ and wasn't able to find them.  I looked at the CarriedCross site and really liked their wallpapers, so if you'll reveal the secret location...

But seriously, I really like what I've seen of the distro so far, your team has done a great job.

Thanks,
SLW 8)

---

### Post by bthumper on 2006-09-26
> **mhancoc7 said:**
> I just tested the iso using the Manual Partitioning and it works great. Have you installed Ubuntu CE before? It may be an issue with Ubuntu in general. Jereme

Used the "Check CD for defects" option and get 3 failed checksum errors. Hmmmm. :???: 

Will try downloading again.

---

### Post by mhancoc7 on 2006-09-27
> **Christian.Sportsman said:**
> Where can the new wallpapers be found?  I looked in /usr/share/ and wasn't able to find them.  I looked at the CarriedCross site and really liked their wallpapers, so if you'll reveal the secret location...

But seriously, I really like what I've seen of the distro so far, your team has done a great job.

Thanks,
SLW 8)

They are located in /usr/share/backgrounds/

Thanks for your kind words. I hope you find Ubuntu CE useful.

God Bless, Jereme

---

### Post by mhancoc7 on 2006-09-27
> **bthumper said:**
> Used the "Check CD for defects" option and get 3 failed checksum errors. Hmmmm. :???: 

Will try downloading again.

I used Reconstructor as well as UCK to create this release. I just read something about getting checksum failures on the Reconstructor site. At least I think it was on the Reconstructor site. I will definitely be looking into this. Thanks and let me know what else you find.

Thanks, Jereme

---

### Post by mhancoc7 on 2006-09-27
> **mhancoc7 said:**
> I used Reconstructor as well as UCK to create this release. I just read something about getting checksum failures on the Reconstructor site. At least I think it was on the Reconstructor site. I will definitely be looking into this. Thanks and let me know what else you find.

Thanks, Jereme

Ok, I was wrong. It is UCK that is causing the issue. Here is the link to the launchpad bug report.
[https://launchpad.net/products/uck/+bug/61600](https://launchpad.net/products/uck/+bug/61600)

I will be following this closely. I am still not sure why you are not able to install with using the Manual Partitioning. 

Thanks, Jereme

---

### Post by mhancoc7 on 2006-09-27
Ok there has been a fix for the UCK script. I will be working to make sure it fixes the issue and if so I will be releasing the fix with the next release which will probably come sooner than I had planned.
Thanks, Jereme

---

### Post by bthumper on 2006-09-27
> **mhancoc7 said:**
> Ok there has been a fix for the UCK script. I will be working to make sure it fixes the issue and if so I will be releasing the fix with the next release which will probably come sooner than I had planned.
Thanks, Jereme

Yep, getting the same results... checksum failures and freezing during partitioning.

Will try it again on the next release.

---

### Post by silvagroup on 2006-10-01
I too got the 3 items check sum error when I did a check cd, however my iso check sum is ok? How can that be? I'll try burning it again to see if it makes any difference.:confused:

---

### Post by mhancoc7 on 2006-10-02
> **silvagroup said:**
> I too got the 3 items check sum error when I did a check cd, however my iso check sum is ok? How can that be? I'll try burning it again to see if it makes any difference.:confused:

I am not sure, but I am wrapping up testing on v1.4 that fixes the issue.
God Bless, Jereme

---

### Post by cre8ivgil on 2006-10-06
> **mhancoc7 said:**
> Yes you can make the changes using your root account (sudo). PM me and I will give you instructions.
God Bless, Jereme
Jeremy,
I am in the same situation, could you provide me with the instructions to unlock the Firefox Proxy as well. I am not able to connect at all. Thanks

---

### Post by mhancoc7 on 2006-10-06
> **cre8ivgil said:**
> Jeremy,
I am in the same situation, could you provide me with the instructions to unlock the Firefox Proxy as well. I am not able to connect at all. Thanks

I just sent you instructions by PM.
Jereme

---

