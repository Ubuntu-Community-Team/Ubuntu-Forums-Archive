---
title: "Question regarding SSH and server setup"
date: 2007-11-16
forum: Server Platforms
---

### Post by bourne- on 2007-11-16
Hello.

I am sort of new to the whole server setup thing. I have been working on setting up servers in school but I am still a little shaking on the whole process.
Basically what I want to be able to do is ssh between one of my schools servers and my machine at home. I would also like to grant access of one other user to be able to ssh into the machine and just use their account that i have setup already.

I understand I think how the ssh client works and everything and I know how to ssh into the server at school and I can also scp stuff to the server. However I am not 100% how to go the other way. 

I used 'apt-get' to put openssh. I have been able to ssh onto the machine running openssh from within the network I am running at home, however I can't ssh into from outside this network.

Currently I have a two router network at the moment. One router is connect to the modem which is receieving an ip from the ISP, then off of t hat router I have another wirless router which has DHCP shut off so it is just acting as a switch. It a wireless router and broadcasts to all the wireless machines in the house. 

So my question is. Is there away that I can have access to a machine with in my network from an outside source? I am not sure if I am explaining it properly. Beacuse the machines in the house get ips from router that are all 192.168..... something something i can't obviously find them on the internet. So is there away that I can someone map the ISP IP that the router gets to point at my machine. Or do I have to have my machine directly connected to the ISP modem and have their IP in order to connect to the machine running the openssh?

The machine I want to connect to is running Ubuntu Fiesty 7.04 and currently holds an IP of 192.168.0.104 from within the home network. The machine is connected to the router that is piggy backing of the router that is directly connected to modem.

I hope I have explained myself well enough, I know this is probably going to sound whacked out, I am just not really sure if I can do what I am proposing. I am sure that I am missing some huge major component but I am just learning so please bare with me. 

Thanks in advance
todd

---

### Post by maybeway36 on 2007-11-16
You just need to port-forward SSH on your router (usually port 22, although it wouldn't hurt to change it for security.) Usually to do this, you go to your router's IP in a web browser.

---

### Post by mellowd on 2007-11-16
You would need to forward the port to your internal ubuntu box. your router will then take anything coming in on port 22 (or whatever you set it to) and forward the packet straight to your ubuntu box. You would use the external ip to connect from outside.

alternatively if you have a hardware firewall you could create a vpn and you wouldnt have to forward the port anymore

---

### Post by bourne- on 2007-11-16
> **mellowd said:**
> You would need to forward the port to your internal ubuntu box. your router will then take anything coming in on port 22 (or whatever you set it to) and forward the packet straight to your ubuntu box. You would use the external ip to connect from outside.

alternatively if you have a hardware firewall you could create a vpn and you wouldnt have to forward the port anymore

Wow that is amazing news that I can actually do that awesome. Um I hate to ask. But is there some place that I can get a tutorial on how to do either one of these steps? Or can one of you guys maybe explain it. I know its a lot to ask I am just not 100% sure on how to do it. I think I understand the port forwarding part...but I am unsure of exactly how to do it.

The VPN option also sounds promising, although I am not sure how to set that up either...not in ubuntu anyways

thanks again for the help
todd

---

### Post by mellowd on 2007-11-16
check [http://portforward.com/](http://portforward.com/) and then look for your router model there. It should be pretty easy because you are only forwarding one port, 22.

---

### Post by mellowd on 2007-11-16
Also, I haven't actually set up a pc to pc vpn yet with ubuntu. I've got a netscreen firewall which I vpn into from work.

---

### Post by bourne- on 2007-11-17
> **mellowd said:**
> Also, I haven't actually set up a pc to pc vpn yet with ubuntu. I've got a netscreen firewall which I vpn into from work.

hmm..i have never heard of that before

umm i was just wondering...you guys had mentioned that using port 22 creates a security risk, and that I could use a little port. I was just wondering what you meant by that? Sorry I know that is probably a stupid question. I am just wondering how it works as I was under the impression that ssh could only run on port 22. When you say use a different port do you mean when i set up the port forwarding under the "public port" i would use 22..but under the private port section i would use a different port?

Also when I set this port forwarding up, would I use the ISP address to ssh onto my linux box?

thanks again
todd

---

### Post by mellowd on 2007-11-17
Yeah, you would use the external ip you get from your isp. your router will then forward any packet that is coming on port 22 straight to your ubuntu box, while doing its normal Nat-ing with any other packet.

I suggest for now just keep it port 22. Once you get that working you can lock your system down later.

---

### Post by bourne- on 2007-11-17
> **mellowd said:**
> Yeah, you would use the external ip you get from your isp. your router will then forward any packet that is coming on port 22 straight to your ubuntu box, while doing its normal Nat-ing with any other packet.

I suggest for now just keep it port 22. Once you get that working you can lock your system down later.

Can you suggest a good site that I can follow to setup the proper security measures? Preferably I would like to set it up so that once the individual has logged  onto my machine I don't want them to be able to see anything outside their home working directory. I know that a security measure I have to set on their account though.

But for like incoming SSH stuff, is there a good site?

thanks for the help thus far

todd

---

### Post by mellowd on 2007-11-17
As long as you set up their user account with access only to their home dirs then you shouldnt have a problem. they can log on via ssh and then they'll be stuck in their home dir.

have you managed to set the port forward up?

---

### Post by bourne- on 2007-11-17
> **mellowd said:**
> As long as you set up their user account with access only to their home dirs then you shouldnt have a problem. they can log on via ssh and then they'll be stuck in their home dir.

have you managed to set the port forward up?

Yes sir indeed I have. I have not yet been able to test it from outside the network. However I wasn't able to do this before: ssh <user>@<isp IP>
which i am able to do now so I am assuming that it is working properly.

Now when you said just make sure that you set their user account with access with their home directory only. Is that something that I would change using something like: 
```
 chmod 750 <account name> 
```

Or am I way off on that? Its been a while since I have had to modify permissions ugh.

Also I had another question, sorry I am just full of these tonight. I have been messing around with how the prompt will look and I have been noticing somethings that seem odd. For some reason if I change the prompt to look a certain way, when I SSH in the PS1 command doesn't recognize any of the special characters and the prompt is set to whatever I typed in. Example:
```

setting this in the .profile file of the users account

PS1="[ \u \w ]$ "

this displays:

[ \u \w ]$ 

instead of:

[ bourne \home\bourne ]$ 

```

I was just wondering if you new why the special prompt was being ignored by SSH. the same goes for aliases. I am able to set them in the .profile file that works alright. But if I try and enable the default ones that are listed in the "./bashrc" file by uncommenting them, nothing happens the user is still unable to use the aliases. I have to set aliases in the .profile file only.

I am also curious as to why 'tabbing' to complete file names does not work

thanks in advance
and thanks thus far for all the help

todd

---

### Post by mellowd on 2007-11-17
To your last question, it should work. What ssh client you using? I use Putty and my prompt looks okay and tab completetion also works. It's a free program so check it out.

---

### Post by bourne- on 2007-11-17
> **mellowd said:**
> To your last question, it should work. What ssh client you using? I use Putty and my prompt looks okay and tab completetion also works. It's a free program so check it out.

Hey man thanks for the advice. I am using SSH Secure Shell, maybe I will give putty a try. Thanks for all the help man.

I was looking into the security issue last night, and I found something called "chroot",  this helps to limit users to their home directories, sounded kind of difficult to setup though, but I will give it a shot. I also think I understand now how to change the port that SSH listens on. So hopefully that will add to the protection as well. The way I have it setup now really isn't good ugh. I tests it from school and you can view like everything currently. So I have disabled SSH for the time being until I can figure out how properly secure it. Thanks a lot again for all your help man

todd

---

### Post by mellowd on 2007-11-17
no problem, glad to help. just remember if you change the ssh port you'll need to forward the new port as well and can probably remove the old forward

---

