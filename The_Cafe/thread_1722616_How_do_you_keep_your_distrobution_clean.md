---
title: "How do you keep your distrobution clean?"
date: 2011-04-06
forum: The Cafe
---

### Post by galacticaboy on 2011-04-06
I would like to know how some of you keep your Linux Distro clean? What do you do to make it sparkle and shine?

Here is what I do, I know some of this may be redundant, but I do it anyway.
1. Run BleachBit in Root mode
2. Run Ubuntu Tweaks Package Cleaner
3. sudo apt-get autoremove
4. Organize all of my desktop icons, files, and folders into clean folders, or take them off my desktop period


I do this about one time a week! So how do you clean your Linux PC? Are there some other ways to keep it super clean?
David

---

### Post by smellyman on 2011-04-06
Put a new distro on every month or so. I just can't help myself and it is just way too easy to do with linux.

---

### Post by NightwishFan on 2011-04-06
I never need maintenance really. I can't think of anything except perhaps Firefox that might need it. At times I have to delete some old files to renew some space on my data drive. I tend to hoard iso images of distributions I try after a while.

---

### Post by VastOne on 2011-04-06
> **galacticaboy said:**
> I would like to know how some of you keep your Linux Distro clean? What do you do to make it sparkle and shine?

Here is what I do, I know some of this may be redundant, but I do it anyway.
1. Run BleachBit in Root mode
2. Run Ubuntu Tweaks Package Cleaner
3. sudo apt-get autoremove
4. Organize all of my desktop icons, files, and folders into clean folders, or take them off my desktop period


I do this about one time a week! So how do you clean your Linux PC? Are there some other ways to keep it super clean?
David

Good advice .. A lot of ppl do not know of some of these tools.. Well done

I also like your sig line, worth repeating and one that lot of users _really need to learn_

People need to learn the difference between an opinion and someone blowing smoke out their behind. When someone gives their opinion, do not tell them they are wrong, or even make them sound like they are wrong. It is an opinion, get over it.

---

### Post by NightwishFan on 2011-04-06
Over and done with.

---

### Post by VastOne on 2011-04-06
> **NightwishFan said:**
> You better not be referring to me.

WTF???? Get over yourself... You happen to see this thread and somehow connect it to you

What am I, some kind of a wizard that would know you would read this?

Why so defensive?

---

### Post by NightwishFan on 2011-04-06
Edit: resolved

---

### Post by VastOne on 2011-04-06
> **galacticaboy said:**
> I would like to know how some of you keep your Linux Distro clean? What do you do to make it sparkle and shine?

Here is what I do, I know some of this may be redundant, but I do it anyway.
1. Run BleachBit in Root mode
2. Run Ubuntu Tweaks Package Cleaner
3. sudo apt-get autoremove
4. Organize all of my desktop icons, files, and folders into clean folders, or take them off my desktop period


I do this about one time a week! So how do you clean your Linux PC? Are there some other ways to keep it super clean?
David

Back on topic, is there any inherent risks to bleachbit that you have come across?

---

### Post by VastOne on 2011-04-06
> **NightwishFan said:**
> Why do you care? :rolleyes: Cya ):P

I do not, just wondering why I am being targeted..

Seems rather immature..

---

### Post by VastOne on 2011-04-06
> **smellyman said:**
> Put a new distro on every month or so. I just can't help myself and it is just way too easy to do with linux.

Yep.. I do the same thing...

---

### Post by inobe on 2011-04-06
i clean every six months, in fact the next cleanup is scheduled for 4-28-11 :P

---

### Post by NightwishFan on 2011-04-06
Over time the /var/cache/apt directory does get a bit cluttered, especially on a rolling distribution. apt-get autoclean is always a good step. You have to be careful about left over virtualbox vms as well, they can add up if you forget to delete them.

---

### Post by Rasa1111 on 2011-04-06
> **galacticaboy said:**
> I would like to know how some of you keep your Linux Distro clean? What do you do to make it sparkle and shine?

Here is what I do, I know some of this may be redundant, but I do it anyway.
1. Run BleachBit in Root mode
2. Run Ubuntu Tweaks Package Cleaner
3. sudo apt-get autoremove
4. Organize all of my desktop icons, files, and folders into clean folders, or take them off my desktop period


I do this about one time a week! So how do you clean your Linux PC? Are there some other ways to keep it super clean?
David

I don't find it much of an issue since Ive been using Ubuntu 
(1 year). 

But when I do "clean up", 
I do a couple things..

1. I use Tweak *usually* (sometimes I use synaptic) and I clean my cache, clean configs, clean old kernals, and any unused PPA's.

2. I ```
sudo apt-get autoclean 
```

3. I remove all old downloads, zips/tar.gz's,/.rars, etc. 

4. I take everything that Ive downloaded, (if I dont *need*(or want)it just sitting on the machine), and I transfer it all to a 1TB external drive, and then remove it from the computer. 

I only do all of these things every few months or so...
But most times, in between the few months, Ill throw in a ```
sudo apt-get autoclean
```, or move some new files over to the external. 

 Keeping Ubuntu clean is like nothing, compared to when I used to attempt to keep my windows clean.  lol

---

### Post by Shmantiv_Radio on 2011-04-06
Bleachbit. The amount of crap it gets rid of is amazing.

---

### Post by wolfen69 on 2011-04-06
> **inobe said:**
> i clean every six months, in fact the next cleanup is scheduled for 4-28-11 :P

This.

---

### Post by Philsoki on 2011-04-06
When I was running Ubuntu I had a habit of doing this from time to time:
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
```
sudo apt-get clean
```

Didn't really need to do it.. Bit I did.

I can't believe some people here do a clean install once a month! On a test machine, yeah, OK. But on a work machine I could hardly be bothered... I guess it would be good practice to back up documents all the time.

---

### Post by galacticaboy on 2011-04-06
> **VastOne said:**
> Back on topic, is there any inherent risks to bleachbit that you have come across?

None so far, it works very well, but when I have every box checked, I will get a message saying that I only have less than 1GB of hard drive space left, but that is because it is cleaning it, not a big deal.

---

### Post by Shmantiv_Radio on 2011-04-06
> **galacticaboy said:**
> will get a message saying that I only have less than 1GB of hard drive space left, but that is because it is cleaning it, not a big deal.

No it's because you've ticked Free Disk Space, which shreds the *free disk space* to hide what's there. It's utterly pointless to tick this option.

---

### Post by user1397 on 2011-04-06
I try to run bleachbit since it seems to take care of most things (even apt-get autoremove, autoclean, etc) once in a while, but that's it as far as OS maintenance

---

### Post by dzon65 on 2011-04-06
Some good cleaning with wajig and deborphan. In script form, it does one hell of cleaning.
Such as:
 apt-get clean
 apt-get autoclean
 apt-get autoremove
 apt-get purge
 delete orphaned packages
 delete residual config files
 delete thumbnails (current user)
 delete thumbnails (root)
 delete mozilla cache (current user)
 delete trash (current user)
 delete trash (root)

---

### Post by vehemoth on 2011-04-06
> **Philsoki said:**
> 
I can't believe some people here do a clean install once a month! On a test machine, yeah, OK. But on a work machine I could hardly be bothered... I guess it would be good practice to back up documents all the time.

I often do, but that's mainly because i stuff up my linux a bit, It's only because linux is so easy to install, it's not like the treading over egg shells that I used to do on windows.

---

### Post by lucazade on 2011-04-06
I use bleachbit once a month maybe, for the rest it is usally clean because I use minimal installation and don't play a lot with software center.

---

### Post by Bluesan on 2011-04-06
> **galacticaboy said:**
> I would like to know how some of you keep your Linux Distro clean? What do you do to make it sparkle and shine?

Here is what I do, I know some of this may be redundant, but I do it anyway.
1. Run BleachBit in Root mode
2. Run Ubuntu Tweaks Package Cleaner
3. sudo apt-get autoremove
4. Organize all of my desktop icons, files, and folders into clean folders, or take them off my desktop period


I do this about one time a week! So how do you clean your Linux PC? **Are there some other ways to keep it super clean?**
David

This "How-to" thread has been around a long time, and is the standard that many use to keep their installs tidy...

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by Philsoki on 2011-04-06
> **Bluesan said:**
> This "How-to" thread has been around a long time, and is the standard that many use to keep their installs tidy...

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
Thankyou, you just reminded me of one of the most important commands know to linux:
```
apt-get moo
```

---

### Post by VastOne on 2011-04-06
> **Philsoki said:**
> 
I can't believe some people here do a clean install once a month! On a test machine, yeah, OK. But on a work machine I could hardly be bothered... I guess it would be good practice to back up documents all the time.


Test partitions, all over the place...

But, if you have your /home on a separate partition and use Synaptic to backup your current applications and restore it on the new install, you are really only talking a matter of minutes to install...

---

### Post by Simian Man on 2011-04-06
My laptop has two hard drives the same size, one has / and swap on it and the other has /home.  The one with / and swap is only 13% full despite having tons of packages installed.  So I really have no reason to try to keep things clean :).

---

### Post by VastOne on 2011-04-06
> **Simian Man said:**
> My laptop has two hard drives the same size, one has / and swap on it and the other has /home.  The one with / and swap is only 13% full despite having tons of packages installed.  So I really have no reason to try to keep things clean :).

You would be amazed at how much "could" be there... 

When I see the real differences is doing a backup, rsync or a dd to another partition..   If I do a cleanup before hand, all those unneeded packages removed makes it a lot smaller!

---

### Post by Simian Man on 2011-04-06
> **VastOne said:**
> When I see the real differences is doing a backup, rsync or a dd to another partition..   If I do a cleanup before hand, all those unneeded packages removed makes it a lot smaller!

Ah yes, if I ever did those things, there would be a reason to cleanup, but I only ever backup stuff in /home.

---

### Post by angry_johnnie on 2011-04-06
i just refrain from installing anything i don´t need.  a few years ago, i would´ve installed everything but the kitchen sink.  one gets a bit more reasonable over time.

---

### Post by Aquix on 2011-04-06
I have one alias that I use often and it also cleans the system

alias sx="sudo aptitude update &&sudo apt-get upgrade &&sudo aptitude dist-upgrade &&sudo apt-get autoclean &&sudo aptitude clean &&sudo apt-get autoremove &&rm -rf /media/sdb/.Trash-1000/* &&rm -rf ~/.local/share/Trash/* &&rm -rf /media/sdc/.Trash-1000/"

Then I install ubuntu tweak when I read about new versions in ubuntu blogs.

Ooh, I also use ppa-purge. awesome little program.

---

### Post by Legendary_Bibo on 2011-04-06
I don't clean anything. I'm a packrat by nature, even on my computer hard drive. I should save a copy of my /home on my bro's external 2tb HDD. I think my HDD is sick now, or at least it sounds like it when I'm using Gimp and playing music, and sometimes the music skips but I think it's because it has to access the swap.

---

### Post by townsy on 2011-09-10
Hi I am fairly new to ubuntu and I use natty narwhal ,I found this article on a gogle site 
which helped me allot I had all sorts of orphaned junk on the os ,aptitude got rid of it via the terminal ,any ways as copied below you may find it will help you get rid of unwanted junk files,


heres the article......

     0     down vote      [favorite]("http://askubuntu.com/questions/57476/unable-to-remove-residual-config-packages-in-synaptic-package-manager#")     **2**
               share [fb]     share [tw]     share [in]  
                                 I am using 11.04 with Synaptic Package Manager (Ver 0.70).  When I select 'Status' and try to delete packages from the 'Not  Installed (residual config)' option, although I can select these old  applications (such as Banshee and Evolution which I don't use) and 'mark  for removal', the 'Apply' button is not active and remains greyed out. I  assume that I am administrator as I am the only user of the machine and  can use the 'sudo' prompt in terminal. What am I doing wrong?
      
                          [synaptic]("http://askubuntu.com/questions/tagged/synaptic")      
                        [link]("http://askubuntu.com/q/57476")[improve this question]("http://askubuntu.com/posts/57476/edit")
                                         asked Aug 17 at 15:51
[URL="http://askubuntu.com/users/23451/andyt"][IMG]http://www.gravatar.com/avatar/35dc7b9a7585273ed9843e1a1d216c0b?s=32&d=identicon&r=PG[/IMG]
[/URL]
[andyt]("http://askubuntu.com/users/23451/andyt")
1

                
          
                    [COLOR=#888888]         feedback     [/COLOR]
                                                     **2 Answers**

                              [active]("http://askubuntu.com/questions/57476/unable-to-remove-residual-config-packages-in-synaptic-package-manager?answertab=active#tab-top") [oldest]("http://askubuntu.com/questions/57476/unable-to-remove-residual-config-packages-in-synaptic-package-manager?answertab=oldest#tab-top") [votes]("http://askubuntu.com/questions/57476/unable-to-remove-residual-config-packages-in-synaptic-package-manager?answertab=votes#tab-top")              
         
     
                                                                  up vote     1     down vote  
                  That is a known bug. You can remove the residual config files without synaptic using this handy one-liner:
  aptitude -F %p search '~c' | xargs dpkg -P   You may have to install [aptitude]("http://packages.ubuntu.com/aptitude")[[IMG]http://bit.ly/software-small[/IMG]]("http://apt.ubuntu.com/p/aptitude") if you haven't done that yet.
 
                        [link]("http://askubuntu.com/questions/57476/unable-to-remove-residual-config-packages-in-synaptic-package-manager/57482#57482")[improve this answer]("http://askubuntu.com/posts/57482/edit")
           edited [Aug 17 at 16:21]("http://askubuntu.com/posts/57482/revisions")
[URL="http://askubuntu.com/users/1992/roland-taylor"][IMG]http://www.gravatar.com/avatar/d629b6ac45d58dbd918c0246b364748d?s=32&d=identicon&r=PG[/IMG]
[/URL]
[Roland Taylor]("http://askubuntu.com/users/1992/roland-taylor")
14.5k21244

                                        answered Aug 17 at 16:20
[URL="http://askubuntu.com/users/15635/exasam"][IMG]http://www.gravatar.com/avatar/98eb24a6fa5b9a55ae5289bc1e44311c?s=32&d=identicon&r=PG[/IMG]
[/URL]
[exasam]("http://askubuntu.com/users/15635/exasam")
37128

                            
                                                          
        sudo aptitude purge ~c is more than enough. – [enzotib]("http://askubuntu.com/users/2647/enzotib") Aug 17 at 16:30
                                  
               [COLOR=#888888]         feedback     [/COLOR]


after I downloaded aptitude  I then used sudo  aptitude purge  ~c it got nrid of masses of junk files I had accumalated!

---

### Post by Erik1984 on 2011-09-10
By doing nothing (cleaning tools and such). Only thing I do is try to organize my home folder and don't leave too much files in the downloads folder, so either delete if I don't need them or put in the appropriate folders.

---

### Post by handy on 2011-09-10
I have an alias in Arch that removes all unused packages from /var/cache/pacman/pkg/

**alias clearcache="sudo pacman -Sc"**

which I do from time to time.

**DotPac**, is a great little tool for cleaning up all of the .pac* files that you can accumulate in Arch.

Apart from the above running Arch allows you to only have installed what you chose to install yourself, so that keeps the system cleaner than most distros out there.

Another thing I do is have my /home & /store partitions pretty well organised & I back them up to a ReadyNAS Duo, (which is also a torrent slave) which isn't so much about keeping the system clean as keeping the data in a more secure fashion & using less power as I can turn off my main machine(s) when I go to bed & the little ReadyNAS can stay on torrenting whilst running on the smell of an oily rag (so to speak).

Also, I use Openbox with no icons on the desktop, & manage my system primarily via Worker. This certainly wouldn't suit most users but it makes it really easy for me to see my directory structure & its contents & to operate on it however I desire.

---

### Post by wojox on 2011-09-10
[IMG]http://www.1stchoicecleaningsupplies.com/images_123/cleaning-products.jpg[/IMG]

---

### Post by Gremlinzzz on 2011-09-10
Bleachbit in root:popcorn:

---

### Post by IWantFroyo on 2011-09-10
I just have a seperate /home partition. Whenever my system gets horribly bloated, I install another distro.

I follow the progress of multiple distros (openSUSE, Fedora, eOS, #!, Debian, etc.), so it's too easy to switch when a new version comes out. Only takes a few minutes. :)

Most of the time, I end up installing something else before my computer can even get some healthy clunk on it. :roll:

---

### Post by ilovelinux33467 on 2011-09-10
On Fedora I just run
```

su -c 'yum clean all'

```

Which cleans cached rpms, package headers, metadata, cached data from rpmdb and yum's sqlite cache used for access to the metadata.

---

### Post by galacticaboy on 2011-09-10
> **wojox said:**
> [img]http://www.1stchoicecleaningsupplies.com/images_123/cleaning-products.jpg[/img]

+1

---

