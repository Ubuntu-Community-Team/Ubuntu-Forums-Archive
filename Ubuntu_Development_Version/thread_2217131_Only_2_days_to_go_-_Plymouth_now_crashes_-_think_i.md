---
title: "Only 2 days to go - Plymouth now crashes - think its since kernel .23 to .24"
date: 2014-04-15
forum: Ubuntu Development Version
---

### Post by 23dornot23d on 2014-04-15
Been running flawlessly ........ and now every reboot .... 

I keep getting two warning boxes - do you want to report this error

[IMG]http://i.minus.com/iPUZM7L6Ke0Gq.png[/IMG]

Plymouthd has crashed ........ yet I can still work ....... only every now and then

the same things appear ......... here is a link to a screen shot - full size ..........

[http://i.minus.com/ibqtLgRTUrqUNg.png](http://i.minus.com/ibqtLgRTUrqUNg.png)

Was booting to or through lightdm as I had autologin set

but just this minute tried kdm to see if the errors would go away ..... but they are still here.

( Have switched over to kdm now to boot ......... but the same messages appear. )


Not sure if its just best to drop back to 2 or 3 days back and use my snapshot of the system

or if this is something that will be fixed in the next couple of days ........

Might just be because I use optimus ....... but who knows .......... 

If anyone knows what to search for in the logs to check .... leave me a quick reply please .......

and I will post any more information ....... meanwhile I will try to send the error in to launchpad.

Cannot send in the report message .......  it all just vanished into thin air ...........

---

### Post by Mateusz Stachowski on 2014-04-15
> **23dornot23d said:**
> 
and I will post any more information ....... meanwhile I will try to send the error in to launchpad.

Cannot send in the report message .......  it all just vanished into thin air ...........

What do you mean by vanished? Those crash reports should be in this directory /var/crash.

---

### Post by 23dornot23d on 2014-04-15
The text from the file is here 
 
_sbin_plymouthd.0.crash

I sent the pastebin of the log - direct to the user above ...... 

[https://bugs.launchpad.net/~stachowski-mateusz/+subscribedbugs](https://bugs.launchpad.net/~stachowski-mateusz/+subscribedbugs)

Hopefully you know how to get it to the right place ...........

---

### Post by sdowney717 on 2014-04-15
I have 20 some crashes, but mostly related to no awaken after sleeping.

I would click report and they would simply vanish off the screen.

I had no idea where they went, but do see them now in var/crash

Some say uploaded, but I wonder because I never followed through with filling in all the details, logging into ubuntu bug web site.

Did they ever go there?

---

### Post by 23dornot23d on 2014-04-15
I have more in there too ........ but they are old ones ....... and they seemed to get resolved as they
never appeared again in updates and upgrades .........

> 
keith@keith-K53SV:/var/crash$ ls
_sbin_plymouthd.0.crash      _usr_bin_baloo_file_extractor.1000.crash
_sbin_plymouthd.0.upload     _usr_bin_compiz.1000.crash
_sbin_plymouthd.0.uploaded   _usr_bin_Xorg.0.crash
_usr_bin_ardesia.1000.crash


But the one I just reported as been with me 2 days now .... but like the rest thought it would soon get
resolved with being at the very start of things ...........

Thing is - you cannot just remove plymouth or step back easily from what I am finding .........

But I do have a snapshot from 4 days back ......... would rather get this sorted though as I do a lot in 4 days.

---

### Post by mc4man on 2014-04-15
That crash is 3 + years old & obviously more  an annoyance than an issue - 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/750405](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/750405)

As mentioned elsewhere  apport reporting to launchpad for crashers has been turned off for 14.04, see [here]("http://ubuntuforums.org/showthread.php?t=2216553&p=12985776&viewfull=1#post12985776") 

Maybe try cleaning out /var/crash/, this should suffice if there are files in there no matter who owns
```
sudo rm /var/crash/*.*
```

---

### Post by sdowney717 on 2014-04-15
Do crash files in /var.crash impact the operation of the OS in any way?

I ask because until I was able to get a successful sleep- wake cycle, (miracle I think) every boot, a system error crash message would pop up. And I would have click it off 11 times for it t finally go away. (after each click a new message)
And it was extremely annoying.

---

### Post by 23dornot23d on 2014-04-15
The crash is new and affects 9 other users ....... and it is being reported here

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1216022](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1216022)

I just added myself to it .........

---

### Post by Redalien0304 on 2014-04-15
same here but only evry so often not today though

---

### Post by 23dornot23d on 2014-04-15
I think I will make a snapshot of my system here ......... 

Then drop back to 4 days ago

Clear out the crash reports

Then see if any appear again ....... because 4 days ago I was not getting these messages on the screen

and they are annoying as I hate errors - but even more I dislike constantly removing pop ups on the screen.

Seem to come up as I am editing or wanting to type things .

It was reported last year on this - [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1216022](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1216022)

                                                      **[SIZE=2]     plymouthd assert failure: plymouthd: ./plugin.c:1304: open_input_source: Assertion `backend != ((void *)0)' failed.    [Edit]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1216022/+edit")[/SIZE]**

                       
[LIST]
[*]     [Ubuntu]("https://launchpad.net/ubuntu") 
[*]     [&#8220;plymouth&#8221; package]("https://launchpad.net/ubuntu/+source/plymouth") 
[*]     [Bugs]("https://bugs.launchpad.net/ubuntu/+source/plymouth") 
[*]     Bug #1216022 
[/LIST]
                                        Reported by       [Zsolt Fatér]("https://launchpad.net/%7Efzs")       on [SIZE=3]2013-08-23[/SIZE]                    

             

So maybe it is old ...... but it is annoying and its got to go ....... why should it just appear over the
last 4 days.

And if you look at the last posters on it in the comments  ....... they are all recent ........... this month

Update .... never got as far as going back to my snapshot .... but the errors stopped flashing up
cannot be sure if it was something I just did ...... with the change to kde login ........
But I have marked it as solved anyway at least for me for now.

---

