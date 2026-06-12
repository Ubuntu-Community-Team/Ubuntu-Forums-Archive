---
title: "Wallpaper and Profile Picture Sync"
date: 2012-04-01
forum: Ubuntu One (CLOSED)
---

### Post by Alexander Langanke on 2012-04-01
I have been trying to implement Idea #29115 (Brainstorm) for myself.

**Quick Summary of what I want to do:**

I have several Ubuntu PCs and Laptops which are very personal devices to  me. I like to have the same wallpaper, user picture, email, Instant  messenger accounts ec. on all my pcs. 
Currently I have to manually keep these in sync very time I change anything.  

I want to creat a function in Ubuntu One that unifies  
- user picture 
- wallpaper 
- general system settings as possible 
- instant messaging  
- etc. 

Into a "me" profile which is synced across all Ubuntu one pcs that  have this feature activated.

---------------------------------------------------------------------------------

I have started trying to implement this for myself. Got it working for  my profile picture by creating a folder called ".usersync" inside the  ubuntu one folder. 

My loginname is "alexander". 

I put my profile picture into the .usersync folder and created a link to it. 

I moved that link into the /var/lib/AccountsService/icons  
folder. 

I renamed the link to "alexander" without the "" and did the same process on my other PCs. 

Now when I change my profile picture to anything but the standard  pictures included in ubuntu, the link is overwritten. The new profile  picture is saved in the .usersync folder instead of the  /var/lib/AccountsService/icons folder and then kept in sync by ubuntu  one. 
My other PCs get the changed file the next time I log in and change  their /var/lib/AccountsService/icons/alexander file accordingly. 

That way I can change my profile picture on one PC and have that change automatically translate to all other PCs.  I know it more of a Hack than a real "function". I just want to show that it is easily doable so that perhaps it can be integrated into Ubuntu One officially (although in a prettier - GUI - way)

Sadly I have not got it to work with the wallpaper yet. gconf does  not save the wallpaper in a location of it's own. At least I have not  found it yet.

 Any pointers would be appreciated!

I will be tackling my entire list one by one. So right now I want to get the wallpaper sync to work.

---

### Post by Alexander Langanke on 2012-04-02
So I just did an experiment.

I assigned an Image "A.jpg" as my wallpaper.
I then deleted that image.
I rebooted my PC.
My Wallpaper was now black.

I gather Ubuntu /gconf does not store the wallpaper in a separate area. 

I am unsure how to get the sync working as the trick I used with the profile picture will not work.

Any Ideas?

---

### Post by Alexander Langanke on 2012-04-02
So I did the next best thing.

I put the wallpaper in the .usersync folder I mentioned above and waited for it to sync.

I then assigned it as my wallpaper on two PCs connected to the same ubuntu one account.

I tried to replace the image file with a file of the exact same name without reassigning my wallpaper via gconf or the settings menu. I had hoped that Ubuntu would just take the wallpaper at the filepath I pointed it to.

Unfortunately.. it did not work.
The Greeter uses the new wallpaper, so it is a partial success but the wallpaper changes back to the old one after logging in. 
How can this be? My first experiment showed that ubuntu does not store the wallpaper somewhere seperate so overwriting it should have worked.

I will test more.. again, help is appreciated.

---

### Post by dgaa1991 on 2013-02-19
> **Alexander Langanke said:**
> So I did the next best thing.

I put the wallpaper in the .usersync folder I mentioned above and waited for it to sync.

I then assigned it as my wallpaper on two PCs connected to the same ubuntu one account.

I tried to replace the image file with a file of the exact same name without reassigning my wallpaper via gconf or the settings menu. I had hoped that Ubuntu would just take the wallpaper at the filepath I pointed it to.

Unfortunately.. it did not work.
The Greeter uses the new wallpaper, so it is a partial success but the wallpaper changes back to the old one after logging in. 
How can this be? My first experiment showed that ubuntu does not store the wallpaper somewhere seperate so overwriting it should have worked.

I will test more.. again, help is appreciated.

sry but i cant help :S

But i will defently follow this post !! 

cool idea about the wallpaper and profile pic sync. just googled it when this came p ;)

---

### Post by offgridguy on 2013-02-19
Moving wallpaper is something i would like to do, no success yet, however in this thread
see post #7, maybe you can make something of this.

[http://ubuntuforums.org/showthread.php?t=2094965&highlight=wallpaper](http://ubuntuforums.org/showthread.php?t=2094965&highlight=wallpaper)

---

### Post by sunfromhere on 2013-03-02
This feature in Ubuntu One would be appreciated. If there's a voting, count me in :)

---

