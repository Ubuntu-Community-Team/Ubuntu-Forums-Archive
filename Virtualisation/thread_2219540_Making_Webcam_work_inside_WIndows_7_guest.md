---
title: "Making Webcam work inside WIndows 7 guest"
date: 2014-04-24
forum: Virtualisation
---

### Post by jon43 on 2014-04-24
I had posted this thread: [http://ubuntuforums.org/showthread.php?t=2219522&p=13000845#post13000845](http://ubuntuforums.org/showthread.php?t=2219522&p=13000845#post13000845) then realized maybe I should be asking the more specific quesiton here instead.

Is there a simple way to get a basic Logitech webcam to work inside of a Windows 7 guest with Kubuntu host? I'm trying to make Yawcam fucntional in the guest machine. 

Any advice is much appreciated. 

Thanks

---

### Post by Warren Hill on 2014-04-25
What VM you using? 

VMware, Virtualbox etc,

and what Version of Kubuntu?

Is the Webcam part of your computer or USB?

---

### Post by jon43 on 2014-04-25
Thanks for the reply Warren. 

I'm using Virtualbox with Kubuntu 14.04 x64 with Windows 7 Home as the guest. 

I actually got the webcam to filter through and be visible in the Windows guest last night. It was even able to stream with yawcam to a browser window inside of the guest.

The confusing part is that once I'm "streaming" with yawcam, it's apparently not making it outside of the machine to the web. When I try to view the camera- either from another computer on my home network with the local address, or on my phone with the public IP address, it's not there. I'm thinking that there is some sort of firewall, or that it's the NAT adapter for the virtual machine? 

Thoughts?

---

### Post by SeijiSensei on 2014-04-25
You can't see a guest from outside the host in NAT mode unless you use something like iptables to tunnel packets through the host.  A much easier solution is to switch the guest's networking mode to "bridged."  Now it will get an address on the host's network when it boots.  Browse [this document](http://www.virtualbox.org/manual/ch06.html) for more details on the various networking modes available in VirtualBox.

---

### Post by jon43 on 2014-04-25
Seiji, thanks a ton for that info!

So in theory, I could switch the network mode to bridged and have it work? Would it be as simple as changing that option in the machine settings on the Vbox control interface? 

I openly admit I was unsure of the difference between the different adapter types to select from. I'll give this a shot when I get home.

---

### Post by jon43 on 2014-04-28
So, I indeed got this working- thanks again Seiji!

Once I changed the network mode to bridged, it was a pretty easy proposition. Was able to view the stream remotely from my phone all weekend, which was nice. 

Just curious- is there any security implication to using bridged vs NAT? Either for the host machine, or for the router it's connected to.

---

### Post by SeijiSensei on 2014-04-28
It's no more insecure than any other machine running behind your router.  

NAT is the most common solution because VirtualBox is primarily used as a desktop client.  In that case you don't need to have the VM be visible anywhere other than from the host computer.  

Running the VM in bridged mode is essentially no different than installing another physical computer on your network.

---

### Post by jon43 on 2014-04-28
Great explaination- good to know!

I suppose that means if I keep using this solution, I should run basic security software on the Windows install. :tongue:

---

