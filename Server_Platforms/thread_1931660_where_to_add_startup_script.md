---
title: "where to add startup script"
date: 2012-02-25
forum: Server Platforms
---

### Post by xclusive585 on 2012-02-25
Hi all, 
Im running 10.04 server (headless)

I have a daemon service that starts on boot, but is very "buggy" and usually will not work (even though it is running). However ```
sudo service [my service] restart
``` fixes the service instantly until the next system boot.

I need this service to start (and work) on boot, without logging in, (in case of power outage or other reasons for restart when I am not available)

So I would like to add my restart command somewhere where It will run automatically on boot, preferably** last**. and of course it needs to run without me logging in (otherwise I'd put it in .bashrc)


[B]SOLUTION (from my post on pg. 3)
[/B]* as others have mentioned this is not a true solution. But rather it is a simple workaround I used to accomplish my goal...

Solved. by crontab!

1: I made a script named "startbash" as root. saved it in new directory "/my"
```
#! /bin/bash

sleep 08
service <myservice> restart 
```    (8 seconds is the sweet  spot, 05 was too soon to consistently work, and 10 seconds was just a  little too long to wait :smile:) 

2. I made the file executable (still as ROOT)```
chmod a+x  /my/startbash
```3. I tested it from command line (as user) to ensure  it works and that I had made no mistakes```
sudo  /my/startbash
```4. I edited the crontab as ROOT```
crontab  -e
```adding this line ```
@reboot /my/startbash
```SOLVED.

Pros: I did NOT end up having to change ANY configuration or init.d  script. This leaves everything on my system "un-hacked". Nice clean fix.
Another pro: I now have a file (startbash) and location (/my) where I  can add any bash scripts I want to be run, I can either add to my  existing file, or create new files and add them to my crontab.

Cons: I wish I had known about crontab and how easy it is to use. :smile:

---

### Post by CharlesA on 2012-02-25
You can add it to /etc/init.d/

Whether or not if requires sudo would depending on what the script does.

I suppose you could throw the command in a root crontab with the @reboot setting.

---

### Post by xclusive585 on 2012-02-26
My only concern is that init.d i'm pretty sure is where the service is started in the first place. Placing the command in a shell script in init.d, how can I be sure it's ran last?

---

### Post by whatthefunk on 2012-02-26
You could try adding a .desktop file in ~/.config/autostart

---

### Post by xclusive585 on 2012-02-26
> **whatthefunk said:**
> You could try adding a .desktop file in ~/.config/autostart

on a server with no gui? :-)

---

### Post by whatthefunk on 2012-02-26
> **xclusive585 said:**
> on a server with no gui? :-)

Haha...didnt read that part!#-o

---

### Post by xclusive585 on 2012-02-26
Init.d isn't gonna work, I don't know how to make sure the script is run late enough, I'm assuming it(my restart command) needs to run at a  runlevel later then when init.d is processed?

---

### Post by spynappels on 2012-02-26
How long is the interval between the service starting and it becoming unresponsive?

If it is a relatively long time, a very ugly but efficient hack is to restart it at an interval less than this in root's crontab by adding 

```
* 00,15,30,45 * * * service <name> restart
```

the above is for 15 minute intervals, adjust to suit.

Might be worth spending some time trying to work out why the service stops working though..

---

### Post by xclusive585 on 2012-02-26
the service doesnt *stop* working. it fails to START working

the service starts, but does not function at any point, until it is restarted by using "sudo service [servicename] restart"
its not an issue of the service stopping, it works great and  indefinitely once it's been restarted. from boot it wont function until  it is manually restarted *once*.

So I need a "hack" to run "service [xxxx] restart" *after* everything else boot wise has been started (or as late as possible)...... and without logging in *headless machine*

I checked the service's init.d and it ends with a self restart, I added  another  one just to try and It did nothing to make the service  work.
I am currently considering rc.local, as it seems that its ran without any login occurring and that's exactly what I'm after here. I just don't know if it will run late enough in the boot to accomplish my goal....

As this is a headless machine I dont want to have to ssh login every time i reboot it, just to restart the service.

---

### Post by Lars Noodén on 2012-02-26
> **xclusive585 said:**
> 
So I need a "hack" to run "service [xxxx] restart" *after* everything else boot wise has been started (or as late as possible)...... and without logging in *headless machine*

Scripts run from /etc/rc.local will be run after all the other scripts at that run level.  Put your restart there.

---

### Post by xclusive585 on 2012-02-26
Sounds good. I'll try it and test it in the am and update then. I hope it works.

thanks man!

---

### Post by kevdog on 2012-02-26
What do you really want to do -- meaning what service do you want to start?  If you want to turn it into an upstart job -- meaning upstart starts the service at boot -- this process isn't very hard.  Upstart effectively does the same as sudo service <name> start on the command line.  When creating an upstart script you can have it respawn if it somehow crashes unexpectedly.  Is this what you want to do??  This method is different than simply adding it to the /etc/rc.local file.

---

### Post by xclusive585 on 2012-02-26
> **kevdog said:**
> What do you really want to do -- meaning what service do you want to start?  If you want to turn it into an upstart job -- meaning upstart starts the service at boot -- this process isn't very hard.  Upstart effectively does the same as sudo service <name> start on the command line.  When creating an upstart script you can have it respawn if it somehow crashes unexpectedly.  Is this what you want to do??  This method is different than simply adding it to the /etc/rc.local file.

The service is already a daemon service started at boot by upstart/init.d. The issue is it fails to start properly. 
It works fine once it's restarted. so "what I really want to do" is  figure out how to restart the service sometime AFTER it's init.d script  is processed.

 This is a headless server meant to do all it's jobs as daemon services... So instead of screwing with the program itself and possibly breaking other things, the best solution in this case is simply to restart the service after everything is booted up. This solves the one and only issue I have and does it without risking the stability of anything, given that it's really a nice working install and everything plays nice. 

once I get that service to restart itself late enough into boot, My work will be done. 

I'm going to try adding "service [xxxxx] restart" to rc.local, as someone mentioned apparently its loaded AFTER all the other init.d scripts

---

### Post by sudodus on 2012-02-26
Another alternative might be to start the script with a pause. For example this command line
```
sleep 60
```
makes it wait for 60 seconds before the next line will be executed. So if you can decide how long you need to wait to be sure it will start or restart properly, it is an easy work-around.

---

### Post by xclusive585 on 2012-02-26
> **sudodus said:**
> Another alternative might be to start the script with a pause. For example this command line
```
sleep 60
```makes it wait for 60 seconds before the next line will be executed. So if you can decide how long you need to wait to be sure it will start or restart properly, it is an easy work-around.

that sounds like another worthwhile option.. hmm

now I just gotta figure out the proper formatting to add a bash command to a init.d script

The last thing I want to do is break a script by changing it the wrong way.
(and the Noob in me comes out....) :-D

---

### Post by sudodus on 2012-02-26
... or a cron job as was also suggested earlier in this thread: You can start a batch file in cron containing

```
#! /bin/bash

sleep 60
sudo service [my service] restart
```

Cron has a very limited environment, so you need full paths to commands and you must specify environment variables, if needed.

---

### Post by xclusive585 on 2012-02-26
So. I edited the rc.local

at the end of the "start  {....." section

I added ```
[service <myservice> restart]
```before the "}" at the end of the "start" in the script

edit, doesnt work. false alarm

Im gonna try a cron job then.

---

### Post by Lars Noodén on 2012-02-26
You're welcome, glad it worked.  One of these days I'm going to look into Upstart, because if I understand correctly that should be able to restart a daemon automatically if it fails.  It's still on my list of things to do for now.

---

### Post by xclusive585 on 2012-02-26
> **Lars Noodén said:**
> You're welcome, glad it worked.  One of these days I'm going to look into Upstart, because if I understand correctly that should be able to restart a daemon automatically if it fails.  It's still on my list of things to do for now.

I don't even think anything is aware my service doesn't start properly. But I know it doesnt work right unless it's restarted (even though it's init.d script forces it to restart after loaded, It's just not happening late enough, blah)

I'm not much for programming, I'm definitely a hardware guy, so this is getting a little over my head, but I'll figure out how to make it work even if I break my install doing it. :-D


I really think the rc.local is the proper place to try what I want to do. Maybe my syntax was just incorrect. I'll play more and post back

---

### Post by xclusive585 on 2012-02-26
So, I ask this (after googling found me nothing usable)

when editing an init.d file, in this case rc.local
If i'm trying to replicate a bash command "service <myservice> restart"

a) where in the rc.local should the command go? i.e. in the start {....} section or just freely at the last line of the script (like i'd do with a config file)

b) do I need a path in the command? i.e. instead of "service <myservice> restart" do I "service /etc/init.d/<myservice> restart"

c) do I need brackets etc around my command?

---

### Post by Lars Noodén on 2012-02-26
a) It should go in /etc/rc.local somewhere before the line 'exit 0'

b) You don't need the path, just the name of the script as it appears in /etc/init.d/, that's where the script [service](http://manpages.ubuntu.com/manpages/oneiric/en/man8/service.8.html) will look.

c) No brackets needed, if your service is apache2, then you could write [font=Courier New]service apache2 restart[/font].  Just to confuse things, you could also write [font=Courier New]/etc/init.d/apache2 restart[/font] to do the same thing.

---

### Post by xclusive585 on 2012-02-26
so, I'm giving up on the init.d route.. nothing I can do to the rc.local gets the service to run at boot. It runs only when I manually issue the "service <x> restart" after boot.  I'm gonna guess nothing in init.d is going to be processed late enough in boot to restart the service in a working fashion. (I know init.d is just a backwards compatible thing and that upstart is what's really doing the work, but that's going from a little over my head to wayyyyy over my head.)

Looking into the cron job option now. :-(

---

### Post by xclusive585 on 2012-02-26
> **sudodus said:**
> Another alternative might be to start the script with a pause. For example this command line
```
sleep 60
```makes it wait for 60 seconds before the next line will be executed. So if you can decide how long you need to wait to be sure it will start or restart properly, it is an easy work-around.

interesting, but if I added that line to my services init.d, wouldn't it just stall the whole boot process waiting for the init.d script to finish?

edit: nevermind, poster intended the wait for a cron job...

---

### Post by sudodus on 2012-02-26
Yes a cron job according to

> **CharlesA said:**
> You can add it to /etc/init.d/

Whether or not if requires sudo would depending on what the script does.

I suppose you could throw the command in a root crontab with the @reboot setting.

That is, enter it to root crontab @reboot

---

### Post by xclusive585 on 2012-02-26
Solved. by crontab!

Earlier I said "looking into the cron job option :-("...
I should have said "looking into the cron job option :-)"

1: I made a script named "startbash" as root. saved it in new directory "/my"
```
#! /bin/bash

sleep 08
service <myservice> restart 
```    (8 seconds is the sweet spot, 05 was too soon to consistently work, and 10 seconds was just a little too long to wait :-)) 

2. I made the file executable (still as ROOT)```
chmod a+x /my/startbash
```3. I tested it from command line (as user) to ensure it works and that I had made no mistakes```
sudo /my/startbash
```4. I edited the crontab as ROOT```
crontab -e
```adding this line ```
@reboot /my/startbash
```SOLVED.

Pros: I did NOT end up having to change ANY configuration or init.d script. This leaves everything on my system "un-hacked". Nice clean fix.
Another pro: I now have a file (startbash) and location (/my) where I can add any bash scripts I want to be run, I can either add to my existing file, or create new files and add them to my crontab.

Cons: I wish I had known about crontab and how easy it is to use. :-)

THANKS guys! much appreciated, it's been great learning with you.

---

### Post by sudodus on 2012-02-26
Congratulations :KS

And thanks for sharing all the details

---

### Post by xclusive585 on 2012-02-26
> **sudodus said:**
> And thanks for sharing all the details
I hate when I stumble on a thread that seems to be going somewhere helpful, and then the OP disappears without letting anyone know what happened or how they made out. :-) One of the most important things about a good thread is that it actually provides help to future visitors and googlers.

now if I could just get vmware to install on this damn server, ;-) but that's a whole other story....

---

### Post by kevdog on 2012-02-27
Seems like you solved it, however....

With your upstart script... You said this was an upstart script originally that either failed to start or didn't start, or crashed and didn't restart.

I'm wondering in your original upstart script file if there is a respawn statement.  You can put parameters on this statement on how many times you want to attempt to respawn the process if it fails.  I'm curious the contents of the original upstart script itself.  Not that I'm knocking your cron solution -- since I use cron all the time, however solving this using upstart only -- since its actually an upstart script your attempting to run via cron -- would be in my opinion a much more elegant solution.

---

### Post by hawkmage on 2012-02-27
I agree with kevdog that even through you got it working it is more of a kludge than a solution.  However there are times when a kludge is what we have to live with.

Since the "service" fails to start properly during boot that would indicate to me that there is a dependency on resource that is not available at that time.  Is there any indication what that resource is?  Are there any logs produced by this service?  If so can you increase the logging to a debug or trace level to see what is going on?

This is one of the biggest advantages of using an Upstart script.  Since Upstart is event driven it is very flexible in dealing with resources that come up or go down after the initial init process.

---

### Post by xclusive585 on 2012-02-27
> **kevdog said:**
> Seems like you solved it, however....

With your upstart script... You said this was an upstart script originally that either failed to start or didn't start, or crashed and didn't restart.

I'm wondering in your original upstart script file if there is a respawn statement.  You can put parameters on this statement on how many times you want to attempt to respawn the process if it fails.  I'm curious the contents of the original upstart script itself.  Not that I'm knocking your cron solution -- since I use cron all the time, however solving this using upstart only -- since its actually an upstart script your attempting to run via cron -- would be in my opinion a much more elegant solution.

If you feel like reading through the mess of messages in this thread... I started out trying to work on an init.d solution. 
The service already does in fact have a statement at the end of its init.d process to restart itself... I had even tried adding another. Even tried editing rc.local, failed. None of those options restarted the service late enough in boot for it to work. (possibly because its a network service?)

And since the service was running (just not properly) at boot, I dont think any sofware in charge of restarting the service would have any way of knowing that it was not working right. It's a buggy daemon, and Im lucky it's working the way it is. I'm just glad I found a way to make it work.

and yes the cron job is processed at part of upstart. Hence why I needed a 8 second delay to make sure my script ran AFTER everything else was loaded. Im sure if I was much better at scripting I could have added a delayed restart command to it's init.d, but I feared that would just hold the whole boot process and continue upstart/init.d after the wait, which would just produce the same original problem, with the added fun of a longer boot.

---

### Post by xclusive585 on 2012-02-27
> **hawkmage said:**
> This is one of the biggest advantages of using an Upstart script.  Since Upstart is event driven it is very flexible in dealing with resources that come up or go down after the initial init process.



upstart has been a source of issues and headache for alot of linux users in my opinion....
and it's straying away from standards used by *all?* other distros...

Upstart could be the very reason this service doesn't work at boot. The service a cross platform linux program, that I'm sure is based on init type startup, which ubuntu's upstart is offering the backwards compatibility for..... When I have the time Ill look into logging and *really* try to figure it out...

Not trying to start a flame war, just saying......

---

### Post by xclusive585 on 2012-02-27
And kludge, I like that word. :-)

Here's the thing. Linux practices would tell you that for a daemon process, you ALWAYS edit its config file, and NOT its init.d. It's probably a good idea IMHO to leave scripts like that "stock", so as to not screw up upgrade-ability, or risk other bugs caused by making changes to something that the developer may expect to be as they wrote it..

That said, that's why just adding a cron job seems like the "cleaner" fix to me..
because everything else is as it was, and it gets to stay that way.

---

### Post by Lars Noodén on 2012-02-27
> **xclusive585 said:**
> 
That said, that's why just adding a restart to a cron job seems like the "cleaner" fix to me..
because everything else is as it was, and it gets to stay that way.

If you only need one restart then [at](http://manpages.ubuntu.com/manpages/oneiric/en/man1/at.1posix.html) would be a better fit.  Again, that could be called from /etc/rc.local  With **at** can use a relative time like 'at now +3 minutes'

---

### Post by hawkmage on 2012-02-27
I agree that Upstart has caused headaches but for dynamic systems like desktop/laptop system that are not as static as s server config the old System V init system has become inadequate to handle things like changing WIFi connections or plugging in/removing external storage.  

Gone are the days where the hardware detected at start up is all that the OS has to deal with.  Other Linux distros are running into this same problem.  Ubuntu just happens to been then one to bite the bullet and be an early adopter and implement an event driven init process.  Upstart is used in Fedora 9 and it also in RedHat 6 and all of the down stream version of it like CentOS 6.  OpenSUSE 11.4 includes Upstart but it not the default.  Also Google's Chrome OS uses Upstart.

So, I would not say that it is straying away from the standards it is just an early adopter.  

With that said there is another player out there for the event driven init process and that is systemd.  This is implemented in Fedora 15 and will eventually get into RedHat.  There is a testing fork of Debian that has systemd so I am not sure if/when it will be seen in Ubuntu.  OpenSUSE 12.1 will be using systemd.

Personally I am very familiar with the SystemV init system and have resisted jumping into Upstart and other event driven init systems since I mainly deal with servers.  But it has come to the point where I see the writing on the walls.

---

### Post by xclusive585 on 2012-02-27
> **hawkmage said:**
> There is a testing fork of Debian that has systemd so I am not sure if/when it will be seen in Ubuntu.  OpenSUSE 12.1 will be using systemd.

I HOPE the debian testing goes somewhere and is adopted.... :-) there's a great reason the best distro's IMHO are debian based. I *buntu for the newer kernals, and wider software repos, and better support. But I also *buntu cause it's built on Debian...

---

### Post by kevdog on 2012-02-27
The funny part about this entire thread is that although its been very detailed as to both the described problem and solution, the original daemon that is causing all the problems was actually never mentioned.  Unlike systemv startup scripts, upstart starts processes asynchronously.  You can put a sleep like statement in an upstart script and this will not delay other processes from starting. If you know the process is dependent on other services, you can specify in the upstart script to not start the script until x and y service is up (this check can be done in the pre-up portion of the script).

Although it would appear I'm a big proponent of upstart, I recently went through this process writing an upstart script from scratch for a daemon.  I found the documentation regarding upstart to actually be very straightforward. Albeit I had to read the documentation about 10 times to wrap my head around it, I found in the end the process for writing the script was very easy.  Reading the documentation and reviewing other upstart scripts already contained in the /etc/init directly really helped.

---

### Post by xclusive585 on 2012-02-28
I avoided mentioning the daemon process name because I didn't want this thread to turn into "get logs for that, edit this, check this forum here for this, see the developers site for this..." etc etc. 

I was looking for a simple way to restart *any* service after boot. And with everyone's help we came to a simple, working, solution. 

That being said, see [here]("http://ubuntuforums.org/showthread.php?p=11724429#post11724429"). I've started a new thread to continue the discussion, in the context of fixing the service (ps3mediaserver) properly.

---

### Post by xclusive585 on 2012-02-28
> **hawkmage said:**
>   Upstart is used in Fedora 9 and it also in RedHat 6 and all of the down stream version of it like CentOS 6.  OpenSUSE 11.4 includes Upstart but it not the default.  Also Google's Chrome OS uses Upstart.

So, I would not say that it is straying away from the standards it is just an early adopter.  

With that said there is another player out there for the event driven init process and that is systemd.  This is implemented in Fedora 15 and will eventually get into RedHat.  There is a testing fork of Debian that has systemd so I am not sure if/when it will be seen in Ubuntu.  OpenSUSE 12.1 will be using systemd.

I did not realize upstart has become so widely used. I guess alot has changed in a few years... (on another note) every device I have from windows laptops to my android phone and beyond, still struggle with changing internet sources. :-) so There is still much work to be done in that department (at least by the makers of the OS's for* those* devices. :-))

---

