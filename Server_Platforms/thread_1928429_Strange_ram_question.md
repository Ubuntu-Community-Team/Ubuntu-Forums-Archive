---
title: "Strange ram question"
date: 2012-02-20
forum: Server Platforms
---

### Post by uk_drifter09 on 2012-02-20
Ok my ubuntu 10.04.3 lts server edition 

installed apt-get install ubuntu-desktop 

and i have 1885mb of ram and 3875 similar to that for swap.

i have done the dev/sda sdb thumb drives to add more swap bringing it to 11GB 

also added a really large /var/swapfile with swapon

i need 16GB of solid ram/swap

currently how i have it so far after a period of time not sure why but my system COMPLETELY locks up in black screen losing all network access ssh access and cannot get out of the blank screensaver 

does anyone happen to know a good way of addign swap and having it more stable.

would making 16   1024mb size swap files work better then one 16gb swap file or what would you suggest. 


16gb swapfile in /var directory.
one 4GB thumb drive
one 2GB thumb drive

are all acting as swap.

any ideas would be great thanks.

---

### Post by trundlenut on 2012-02-20
When running is the machine actually using swap?  If so how much?

I think a better idea would be to increase the amount of ram in the machine.

---

### Post by Bucky Ball on 2012-02-20
> **trundlenut said:**
> When running is the machine actually using swap?  If so how much?

I think a better idea would be to increase the amount of ram in the machine.

+1. All sounds a little convoluted.

---

### Post by uk_drifter09 on 2012-02-20
well thats just it at the moment i cant afford to get new ram to upgrade it but 45mb give or take is left on ram and then over 7GB of swap is being used at the moment without crash if i use up to 16 and run everything i need to be running it will get up to 10GB and eventually gets up to 16GB but has never capped out on swap ever it just freezes and have to hard reboot

---

### Post by snowpine on 2012-02-20
Obviously there is something weird going on, like a memory leak. What you need to do is use **top** (or your favorite system monitor) to determine what is using all that memory. I have never heard of an Ubuntu install using 1gb of RAM plus 16gb of swap, that's crazy! Do I understand correctly that you are using USB flash drives for swap??

Your goal should be to reduce your usage to under your 1gb of physical RAM. That will give the best performance (swap is very slow by nature).

---

### Post by arrrghhh on 2012-02-20
Yea, there's some serious memory leak going on.

Is this a new install?  Did it just start happening?  You might want to strip it down to the basics.

Also, why are you doing apt-get install ubuntu-desktop?  You just ruined your server installation.  If you want Ubuntu Desktop, install Ubuntu Desktop.  If you want a server w/o a GUI, install Ubuntu Server.

Seriously.  There's no point in installing Ubuntu Server, then doing an apt-get install ubuntu-desktop.  Some have gone thru the pain of setting up a GUI that's lightweight like LXDE, but I honestly don't see the point.  You can manage a server remotely, no need for a DE... That just wastes resources that you are obviously lean on!!

---

### Post by uk_drifter09 on 2012-02-20
1 4G USB stick and 1 2GB USB stick.
 
and 16GB /var/swapfile    
 
dont think its a memory leak. its a game server and running at full capacity it takes around 10GB ram unless theres a bunch of people playing on it

---

### Post by snowpine on 2012-02-20
I think it's just a case of "not the right tool for the job," sorry. If your app requires 10gb ram, you can't simulate that reliably with 1gb ram and some thumb drives. :( But I am not a game server expert, I don't want to give you bad/wrong advice...

---

### Post by uk_drifter09 on 2012-02-20
well it used to work and i did find a thread before that it had something to do with the desktop i installed and i did something before and it never froze up
 
i dont think its the swap that could be causing it
 
does this sound familiar?

---

### Post by snowpine on 2012-02-20
You need to use **top** and look at some actual numbers.

---

### Post by arrrghhh on 2012-02-20
> **uk_drifter09 said:**
> 1 4G USB stick and 1 2GB USB stick.
 
and 16GB /var/swapfile    
 
dont think its a memory leak. its a game server and running at full capacity it takes around 10GB ram unless theres a bunch of people playing on it

lol.  You're just going to burn out those flash drives, you realize that yes?

Just buy the RAM.  If it needs 10gb, don't give it 1...

 Also, did you ignore the part about ubuntu-desktop?  Do **not** install that package on Ubuntu Server.  There's no point, it's a complete waste of time and resources.

---

### Post by uk_drifter09 on 2012-02-20
> **arrrghhh said:**
> lol. You're just going to burn out those flash drives, you realize that yes?
 
Just buy the RAM. If it needs 10gb, don't give it 1...
 
Also, did you ignore the part about ubuntu-desktop? Do **not** install that package on Ubuntu Server. There's no point, it's a complete waste of time and resources.
 
 
had no choice had to get the desktop so that i can get that auto update for my wireless driver to get updated
but ifi  knew how to get back to terminal only that would help not the desktop background with terminal i mean strait black screen with flashing bar saying login

---

### Post by uk_drifter09 on 2012-02-20
also being able to connected my wireless with the passcode wpa2 or whatever the hell its called

---

### Post by arrrghhh on 2012-02-20
> **uk_drifter09 said:**
> had no choice had to get the desktop so that i can get that auto update for my wireless driver to get updated
but ifi  knew how to get back to terminal only that would help not the desktop background with terminal i mean strait black screen with flashing bar saying login

> **uk_drifter09 said:**
> also being able to connected my wireless with the passcode wpa2 or whatever the hell its called

You're running it on wireless?  bwhahahahahahahaha, dude just install the Desktop Edition.  You're not running a server.

---

### Post by trundlenut on 2012-02-21
Nevermind trying to hammer a square peg into a round hole, you seem to be trying to hammer in a chicken.

Have you thought that the problem could be that one or more of the flash drives are failing?  Given the ratio of ram to swap they must be getting absolutely hammered with constant reads and writes.

It could be coincidence that this problem occurred when you installed ubuntu-desktop or you have increased your memory usage even more and it is having issues swapping.

---

### Post by roelforg on 2012-02-21
I'm gonna take a stab;
 
My pc (ubuntu server 11.10 and i added gui myself (i like to be able to decide for myself how it's gonna look; nothing better than a blank canvas (analogy for: linux system which i can make look/work like i want yet still have all the power from the distro that is Ubuntu)) used ot have 256mb ram;
it used it's few gig swap all the time, this would cause problems.
 
An example is when i open firefox (ram usage: 128mb) and open a site with loads of graphics it started to swap heavy!!! You couldn't get in because it couldn't start any program until firefox would have stopped swapping (consumes loads of CPU and blocks other progs). I could usually fix this by unplugging net and waiting for FF to time out. I guess this is true for all cases where you need more ram than you have. (recently 4x the mem; runs a lot better now!)

---

### Post by arrrghhh on 2012-02-21
> **roelforg said:**
> I'm gonna take a stab;
 
My pc (ubuntu server 11.10 and i added gui myself (i like to be able to decide for myself how it's gonna look; nothing better than a blank canvas (analogy for: linux system which i can make look/work like i want yet still have all the power from the distro that is Ubuntu)) used ot have 256mb ram;
it used it's few gig swap all the time, this would cause problems.
 
An example is when i open firefox (ram usage: 128mb) and open a site with loads of graphics it started to swap heavy!!! You couldn't get in because it couldn't start any program until firefox would have stopped swapping (consumes loads of CPU and blocks other progs). I could usually fix this by unplugging net and waiting for FF to time out. I guess this is true for all cases where you need more ram than you have. (recently 4x the mem; runs a lot better now!)

Running Firefox on a server too?  Yeesh.  You guys really aren't running servers are you....

Everyone realizes you can run the same server 'services' on the Desktop Edition, right!?!?

There's really no point in installing the ubuntu-desktop package on the Server Edition.  Don't do it!!  Just install the Desktop edition from the get-go.  If you feel you need a UI, then you certainly don't need the Server Edition.

---

### Post by roelforg on 2012-02-21
> **arrrghhh said:**
> Running Firefox on a server too?  Yeesh.  You guys really aren't running servers are you....

Everyone realizes you can run the same server 'services' on the Desktop Edition, right!?!?

There's really no point in installing the ubuntu-desktop package on the Server Edition.  Don't do it!!  Just install the Desktop edition from the get-go.  If you feel you need a UI, then you certainly don't need the Server Edition.

May i tell you that my pc's don't have a lot of ram?
I like to use the server version as it allows me to design the graphical side to my likes and not leave any unwanted default stuff.
+ I like my own GUI setup much better than the ones on the normal ubuntu versions (lubuntu,kubuntu,Xubuntu included).

FYI: Who said this is a server? And who said my reasons for using the Server version have anything to do with the 'services' (as you call them, i just call them daemons) i can or (as you say) cannot run on this thing?

---

### Post by roelforg on 2012-02-21
> **roelforg said:**
> May i tell you that my pc's don't have a lot of ram?
I like to use the server version as it allows me to design the graphical side to my likes and not leave any unwanted default stuff.
+ I like my own GUI setup much better than the ones on the normal ubuntu versions (lubuntu,kubuntu,Xubuntu included).

Mem stats:
With FF open (8 tabs): 325mb ram.
W/O FF: 170 mb ram.

This is with a fully graphical system on a pentium IV.
Try pulling that off with the normal versions and still have a smooth running system.
I once tried to use standard ubuntu, unity kept freezing and took well over 4 minutes to come up with the app selection "home screen", the pc was fully booted.
This setup has delays in the milliseconds, on the same PC!


+ I like to think of the server version as a blank canvas, you've got all the power/support/info/every good thing about ubuntu, yet you can decorate it to your likes!

So, Yes i use the server version and no this pc wasn't even meant to be used as a server!
(My home server runs Ubuntu Server too, it uses Ubuntu Server as a server (only access: ssh/web/git/ftp...).
Linux is the O/S of freedom! So let me be free to choose wherether i use the server version and mold that raw block of linux goodness to my own likes or use the standard one which is too heavy (as in: requires so much resources that it keeps freezing) to run on my pc at all!

+ I like the CLI a lot; do most of my work in a terminal;
I use a heavily modded LXDE/XDM combi, works great and (thanks to the mods) looks great too!

I don't need LibreOffice, i never use it, so i didn't install it.

So maybe i don't have all those fancy config apps, i don't want them! I prefer setting up NIC's with /etc/network/interfaces; much more control!

I'm gonna expect a rant for enabeling the root account.

---

### Post by arrrghhh on 2012-02-21
> **roelforg said:**
> This is with a fully graphical system on a pentium IV.

Hooray for you?

> **roelforg said:**
> I'm gonna expect a rant for enabeling the root account.

Meh, you can be dumb with your own equipment.  Just so long as you realize you're being dumb, that's what really matters.

Edit - I also thought you were just blindly installing the ubuntu-desktop package.  What you're doing is quite a bit better than that... If you read the OP, you can see he did this already.  Just ruined his server install.

---

### Post by roelforg on 2012-02-21
> **arrrghhh said:**
> Hooray for you?



Meh, you can be dumb with your own equipment.  Just so long as you realize you're being dumb, that's what really matters.
Give me 1 example of a major public facing webserver that doesn't have one.
Here in linux-land we're all free to make our own decisions.
And keep in mind that i build all my pc's from parts i got for free.
I'm happy, and i'm gonna ignore your comments on my setup as they don't have anything to do with the thread-subject.

---

### Post by arrrghhh on 2012-02-21
> **roelforg said:**
> Give me 1 example of a major public facing webserver that doesn't have one.
Here in linux-land we're all free to make our own decisions.
And keep in mind that i build all my pc's from parts i got for free.
I'm happy, and i'm gonna ignore your comments on my setup as they don't have anything to do with the thread-subject.

You think public facing webservers have DE's?

You're kidding yourself.  Some might have a control panel that's web-based, but that's a far cry from a DE...

None of our webservers have DE's.  Most don't even have webUI control panels.

Of course you can make your own decisions, I already stated that the way you did it was much better than the OP's.  Blindly installing ubuntu-desktop is a complete waste.

---

### Post by roelforg on 2012-02-21
> **arrrghhh said:**
> You think public facing webservers have DE's?

You're kidding yourself.  Some might have a control panel that's web-based, but that's a far cry from a DE...

None of our webservers have DE's.  Most don't even have webUI control panels.

Of course you can make your own decisions, I already stated that the way you did it was much better than the OP's.  Blindly installing ubuntu-desktop is a complete waste.

May i note i was referring to your comment on me enabeling the root account?

And thanks, for that complement about me DE.

---

### Post by snowpine on 2012-02-21
Enabling root account is fine, we just aren't allowed to post how-to tutorials here on ubuntuforums. :)

---

### Post by roelforg on 2012-02-21
> **snowpine said:**
> Enabling root account is fine, we just aren't allowed to post how-to tutorials here on ubuntuforums. :)
I know, i use a customized install disk for that, used kickstart to have it setup accounts/hd/etc.
But can we pleaaaaseeeee get back on subject?

---

### Post by arrrghhh on 2012-02-21
> **roelforg said:**
> But can we pleaaaaseeeee get back on subject?

OP hasn't posted back in a while.  How is your rig OP?  It really sounds like you need more RAM.  Many have already stated, if you have an application that you know requires 10gb+ of RAM, install more RAM!

Good luck.

---

