---
title: "[IDEA] - Disable IPv6 by default"
date: 2007-10-21
forum: Ubuntu Brainstorm
---

### Post by kevdog on 2007-10-21
How about disabling IPv6 by default, but making an easy way to activate this is some users need this feature. I mostly hang out in the networking section (not in this forum sadly) and can't tell you how many connectivity problems are solved by disabling ipv6.

---

### Post by Megatog615 on 2007-10-21
I like this idea. However, on a side note, doesn't disabling IPV6 on the router end mitigate the network issues?

---

### Post by kevdog on 2007-10-21
I dont know enough about this, however, Ive seen a lot of people having to disable ipv6 within firefox to get it to work.  Again Im not very knowledgable about how this fix actually works (some association with router??), Im just telling you this fix has worked many many times.

---

### Post by BungaMan on 2007-10-23
Eventually all should change to IPv6.  If it is disabled by default then no one will ever switch.  Don't count on this being implemented.

---

### Post by handy on 2007-10-23
It's another one of those easy when you know how problems.  

Perhaps mentioning during the install process that there is a document with easy answers to commonly experienced problems that should be read by all new users, & giving it an icon for easy access.

---

### Post by kevdog on 2007-10-23
Again I know some people may want ipv6, but the far majority do not!  I hear of all this eventually stuff, but when is this going to happen, particularly for home based users!!

Again it seems like a simple menu toggle should be added (or something like this), that could easily toggle ipv6 of/off would be sufficient.  

If you have ever done any networking troubleshooting, this would be a very welcome addition!

---

### Post by handy on 2007-10-23
All I have ever needed to do with IPv6 in the *buntu's is the about:config thing in FF.

I expect others may want to disable IPv6 system wide which is not as simple & quick.

For those that only need to tamper with Firefox, I don't think any more than being told to change the about:config IPv6 setting to true is required.

---

### Post by insane_alien on 2007-10-23
what about those of us who do connect to IPv6 networks from time to time?

maybe if we had a little tick box somewhere that would enable/disable it. or even an option in the installer(under an advanced tab or something obviously)

---

### Post by Gorlith on 2007-10-23
The goal is for IPv6 to become the standard, this is not going to happen over night though. Personally I believe it will happen when people decide to leave it on.

Could you tell me what connection issues IPv6 has been causing? I haven't had any and I'm interested to hear.

---

### Post by litemotiv on 2007-10-23
> **Gorlith said:**
> 
Could you tell me what connection issues IPv6 has been causing? I haven't had any and I'm interested to hear.

on gutsy testing (don't know if this still applies) dns-lookups became incredibly slow on some nic/router/dns combinations (don't know which was the exact culprit ;))

---

### Post by insane_alien on 2007-10-23
the way the protocols are working now it tries to talk to the routers with IPv6 first this results in a no reply as the software on the other end is going 'what the hell is that garbage?' because it can't understand the packets. this takes a while for the IPv6 stack to recognise it's talking chinese to a french guy and decides to try speaking french to see if that helps. 

basically, it slows everything down massively in many cases.

if IPv6 is available over the network then it flies and can be much faster than IPv4.

---

### Post by BungaMan on 2007-10-23
> **Gorlith said:**
> The goal is for IPv6 to become the standard, this is not going to happen over night though. Personally I believe it will happen when people decide to leave it on.

Could you tell me what connection issues IPv6 has been causing? I haven't had any and I'm interested to hear.

It is not that dns resolution is slow.  It simply fails because a lot of ISP's don't support it yet in their dns servers, at least mine doesn't.  So the ipv6 dns request times out first and then the ipv4 dns request kicks in.  This is a very noticable delay that people don't like.  Hence the complaining on the forum.

---

### Post by zsouthboy on 2007-10-23
Note that this happens in Vista as well - ipv6 is enabled by default.

There's an extra delay looking DNS the first time.

Complain to your ISP for not supporting the future.

---

### Post by kevdog on 2007-10-23
Tell me any ISP that uses IPv6 -- I serious.  Preferrably one in the US (b/c thats where Im located)

---

### Post by zeronothing on 2007-10-23
hey guys,

if you would like to disable IPv6 from being used not only should you disable it from firefox but you should also disable it in the system as well. Their is no reason to have IPv6 enable right now, unless you in a foreign country that supports it but here in the united states i believe no one uses it (talking about the general public). to disable it go through these steps.

1.) open terminal

2.) sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases_backup

3.) sudo gedit /etc/modprobe.d/aliases

4.) find the section "alias net-pf-10 ipv6" change it to "alias net-pf-10 off"

5.) reboot your pc

after all of that ipv6 will be disabled on the system not just in firefox. if you have ever done the command ifconfig you will have noticed an output mentioning ipv6's information. after doing this how-to you will no longer see ipv6 mention, meaning its disabled. have fun everyone.

---

### Post by zeronothing on 2007-10-23
oh, I also forgot to tell you how to re-enable ipv6. to do that all you have to do is copy your aliases_backup to aliases. 

1.) open terminal 

2.) sudo cp /etc/modprobe.d/aliases_backup /etc/modprobe.d/aliases

3. reboot your pc

then ipv6 should then be re-enabled. to check do the command ifconfig and look under your Ethernet connection for ipv6 information.

---

### Post by handy on 2007-10-24
I lifted this from another thread, it's benefit is that it won't be overwritten as aliases can be.

To disable IPv6 globally:

1. Verify that the IPv6 module is loaded. From a terminal type:
dbott@thedrake:~$ lsmod | grep ipv6
ipv6 265856 10

2. From a terminal type:
sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6

3. Restart

4. Verify that the IPv6 module is not loaded. From a terminal type:
dbott@thedrake:~$ lsmod | grep ipv6
dbott@thedrake:~$

I tested it on Kubuntu 7.10 it works fine.

Perhaps someone who wanted a quick on off switch for this could write a script. Hopefully bringing the network down & up will save having to reboot?

---

### Post by wieman01 on 2007-10-24
Is IPV6 still an issue? I used to have that problem in Breezy and Dapper, but since Feisty I have not had to blacklist the module. Strange that you would have issue with that.

---

### Post by handy on 2007-10-24
> **wieman01 said:**
> Is IPV6 still an issue? I used to have that problem in Breezy and Dapper, but since Feisty I have not had to blacklist the module. Strange that you would have issue with that.

Yes, its still raising its head, causing slow downs & worse.  I'll talk to my ISP & see what they have to say, they may even be able to route me via IPv6 if I'm lucky.  It is possible if we talk to them things will change quicker...

It would surely be appreciated by many, if some smart programmer worked out how to test for both protocols simultaneously, or there abouts, choosing 6 if its available & going to 4 if not.  I know I don't know what I'm talking about, & more time is required for the test.  Oh well.

---

### Post by litemotiv on 2007-10-24
> **handy said:**
> Yes, its still raising its head, causing slow downs & worse.  I'll talk to my ISP & see what they have to say, they may even be able to route me via IPv6 if I'm lucky.  It is possible if we talk to them things will change quicker...

It would surely be appreciated by many, if some smart programmer worked out how to test for both protocols simultaneously, or there abouts, choosing 6 if its available & going to 4 if not.  I know I don't know what I'm talking about, & more time is required for the test.  Oh well.

for the time being, reversing the chain would probably be a better idea; route through ipv4 first, and if that fails try ipv6..

---

### Post by handy on 2007-10-24
> **litemotiv said:**
> for the time being, reversing the chain would probably be a better idea; route through ipv4 first, and if that fails try ipv6..

Yes, I totally agree.

Or what if when you initially install *buntu, it looks to see which protocol your connection is using & asks you if you want it to configure your machine for IPv? whatever it finds?

It could also at this point give a basic education on the topic for those that need it & notify the person doing the installation of the whereabouts on your machine of a document with all the required info' regarding setting one protocol, the other or both.

Which could make it a lot more efficient for those with notebooks that jump around from home to work & wherever else.

I am starting to agree with the initial poster of this thread, if a choice could be made in network settings it would be very convenient for many users, especially notebook users, the IPv4/6 problem is not going to disappear in a hurry.

---

### Post by handy on 2007-10-25
I just had a look at the Sabayon /etc/modprobe.d/blacklist file & ipv6 is NOT blacklisted, nor is ipv6 turned off in Firefox, & this machine does not experience any of the internet slowdown problems running Sabayon as it does with the *buntu's.

I was under the impression that this problem was due to the common windows-centric modem/routers in combination with a user being supplied by their ISP with ipv4.

Is this problem inherited from Debian, is it to do with the kernel or the ipv6 module, Sabayon 3.4f is running 2.6.22, why does this problem exist in Ubuntu?

---

### Post by kevdog on 2007-10-25
How do you like Sabayon??  I was going to try this distro next b/c I fear Gentoo might be a little out of my league!

---

### Post by handy on 2007-10-26
> **kevdog said:**
> How do you like Sabayon??  I was going to try this distro next b/c I fear Gentoo might be a little out of my league!

I like Sabayon a lot.  

For the past 3 months I had been using 3.4a, up until 10 days or so ago, when I discovered that beagled.helper was using about 80% of my cpu time when it should have been idling? I never even use Beagle! 

So I tried 3.4f which still has a similar problem.

Being in an adventurous mood & decided to install Gentoo, which was great fun but there was no way I could get any type of X to install on my machine, the Gentoo forum did not have an answer, I am thinking that it could actually be a BIOS motherboard issue.  So then I had a go at Arch, which went great up until it was time to do the initial upgrade of the system which is when dependency hell unleashed itself causing me to retire doubly defeated & think that I'll settle with having 2 Kubuntu 7.10 machines for a while.  Which led me to discover that it would seem Kubuntu's kernel/modules & my motherboard/bios/AGP GeForce 7950 GT /512, do not get along, ([***_see post 297 here_***]("http://ubuntuforums.org/showthread.php?p=3625767#post3625767")) so I stuck Sabayon 3.4f back on, which is quick, easy & everything works.  There are a few bugs floating around but they don't really bother me, & I'm not even going to think about the cpu thing, I'll hang in there until 3.5 comes out which will have hopefully solved that bug.

Using portage the Gentoo package management system just takes a little getting used  to, the documentation on the Sabayon & Gentoo Wiki's is excellent, their forums are too.  Not as excellent as the Ubuntu forums of course :-) they just don't have the numbers.

Sabayon is heading towards the incorporation of a binary install system called Entropy, it will be available alongside Portage which will always be slower because it compiles every package & its dependencies for your system's hardware - that is the Gentoo way.

I would strongly suggest using Sabayon, it is a gentle introduction to Gentoo, which is exactly what Sabayon is built on, similar in that way to Ubuntu & Debian's build relationship.

So as you may well understand I've currently had my fill of OS installation & setup.  See where adventurous feelings can get you! :lolflag:

---

### Post by handy on 2007-10-26
I just looked further into my Sabayon installation & found that the reason there is no problems with IPv6 is that it doesn't even contain the module.

Which begs the question, on installation does it check on what type of connection you have & act accordingly?

I'll pursue this on the Sabayon forum.

---

### Post by handy on 2007-10-27
It would seem that Sabayon doesn't use IPv6 by default.  There is no module, it is not blacklisted or blocked in the aliases file, the ***lsmod | grep ipv6*** command gives no result, so it is not part of the kernel.

A simple solution to help all those Ubuntu users who are affected by this problem would be to ship with the module installed but blacklisted & supply documentation so those few that actually can use IPv6 can just uncomment a line & reboot to gain access to it.

Does anyone have valid statistics on where IPv6 is available on our planet?

Having had a brief look at a Cisco site the Wiki & elsewhere, it seems like not too many are in a rush to move to the new protocol, it is inevitable but not imperative yet.

---

### Post by insane_alien on 2007-10-27
> Does anyone have valid statistics on where IPv6 is available on our planet?

i don't have any statistics on it but i know that a lot of universities support it. JANET(a uk university network) is all IPv6

---

### Post by kevdog on 2007-10-27
Im not aware of any home based commercial router that uses ipv6 -- and this will probably not be implemented until Im dead!

Again seems like adding a toggle button in the networking menu that would run a script to load/unload the ipv6 kernel module would be the way to go!!

---

### Post by insane_alien on 2007-10-27
i wish they would hurry up and start switching to ipv6. the backbone can already handle it. just the ISP's and home users that have to change.

---

### Post by handy on 2007-10-27
> **insane_alien said:**
> i don't have any statistics on it but i know that a lot of universities support it. JANET(a uk university network) is all IPv6

Yes I read that there were various universities around the world trialling it.

---

### Post by handy on 2007-10-27
> **kevdog said:**
> Im not aware of any home based commercial router that uses ipv6 -- and this will probably not be implemented until Im dead!

Again seems like adding a toggle button in the networking menu that would run a script to load/unload the ipv6 kernel module would be the way to go!!

Yes, the more expensive routers are able to easily have their firmware flashed to upgrade to IPv6.

Really I don't think there is any need to even have your *button* at this stage of the game.  Any of the few who are using IPv6 surely won't have any trouble removing a "#" from a line in the blacklist file & rebooting.

I think that Sabayon has done it right for the time being, they don't even have the module present!  If someone needs it then they can make another kernel to support it internally or via module.

Due to some universities using Ubuntu, I think that the next version of Ubuntu should support IPv4 by default & carry the blacklisted module for those that need it.  This policy will cause the minimum inconvenience to users as opposed to the many new users trying to work out why they can't browse the web, or why they have to wait so long to connect to a new server, all of which can really ramp up the stress level on a new OS, most especially if you have just jumped ship from the MS world.

I don't understand why IPv6 is run as default on Ubuntu, it is in OS-X, & now in Vista as well I believe.  Which doesn't make sense to me at all. :confused:  

IPv6 as an option is plenty good enough.

---

### Post by Prometheum on 2007-10-28
Most of Japan and a lot of China use IPv6.

This is why kernel modules were invented, guys.

---

### Post by kevdog on 2007-10-28
Cater to the majority - not minority -- I think this point has been made already in this thread.

---

### Post by handy on 2007-10-28
Perhaps the pursuit of the ever growing use by the Chinese population of broadband is a prime motivation?

---

