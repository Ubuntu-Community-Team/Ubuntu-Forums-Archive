---
title: "Boot Directly to Full screen XP VirtualGuest"
date: 2011-07-21
forum: Virtualisation
---

### Post by Chiphead2011 on 2011-07-21
Hello all, 
 
I have spent a better part of my day searching for a post that answers my question(s) and have not found enough information so I am now posting the remainder of my questions with a brief description of my situation.
 
Description:
I am an I.T. Administrator and I am attempting to redo the deployment configuration of our mobile users machines. 
I want to install Linux (favoring ubuntu) on the machine, boot linux on the machine so that it will "auto login" (invisible/seamless) as a generic user that launches a Virtual Machine guest of XP in Fullscreen so that the average person using the machine is made to think they are booting into Windows. 
 
 

Goals:
[LIST]
[*]Conceal Linux from the users as much as possible where they are not required to login to the machine or otherwise interact with the Linux OS
[*]Make the machine shutdown when the guest XP machine is shutdown
[*]Allow the guest machine to utilize the USB/Video ports
[*]Be capable of multiple displays
[*]Ability to efficiently run Google Earth and other "3D"-ish apps (no games) inside the VM
[*]Other items that don't come to mind at the moment
[*]Basically try to make the machine function almost as if Ubuntu isn't even there.
[/LIST]The catalyst for this idea is two from different objectives.
1) Web content filtering
2) Utilize a rollback system from the snapshots to potentially revert to a "clean" state on every reboot.
 
We are currently subscribing to a proxied web filtering system through McAfee and our mobile users are the "most difficult" to protect. 
Problem #1 users are admins of their machines. (I know, bad idea! Not something I can do much about right now) This means they can install any web browser that they choose. Policies are forthcoming regarding this but a policy only provides a means to discipline it doesn't stop anyone from doing anything. 
Problem #2 I can AD group policy force the Proxy settings but that will only work for the programs that respect the IE network settings and don't allow you to bypass that and connect directly. Monitoring their machines for new application installation is not something I really want as a new task.
 
My idea is to utilize the ubuntu environment to transparently proxy all web traffic as well as firewall the VM so that problem #1 and problem #2 are not as dangerous where web surfing is concerned. The ability to rollback the previous snapshot / discard changes on reboot helps keep a nice clean lean running machine as well.
 
So...... am I crazy!?! :???:
 
Someone have an idea that will work better?
 
If I ran a VM of ubuntu as a guest on Windows could I use the ubuntu machine as a bridged proxy (using Squid, of course) to at least filter the traffic?

---

