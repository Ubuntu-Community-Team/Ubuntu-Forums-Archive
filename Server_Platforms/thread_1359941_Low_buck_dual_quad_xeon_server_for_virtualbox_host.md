---
title: "Low buck dual quad xeon server for virtualbox host"
date: 2009-12-20
forum: Server Platforms
---

### Post by joker535 on 2009-12-20
I need to build a box to run multiple concurrent vbox machines. I intend to build a network of virtual machines within this single host to test some ideas for work. I am going to be doing this on an ultra tight budget using some decent but not cutting edge hardware. I have done some research and found that the cheapest quad core xeons are the E5310s which would be fine for what I need (~300 for a pair used). I would run 8G of ram (2G for host, 1G for each virtual) initially and add more later if needed (~$180 used) and use an Intel S5000PSLSATA board which is available new for $100. The board does not have the revision for the newer processors which makes it cheap and is fine with me since I'm not using them. I have the rest of the items like psu, drives and such so theres no other cost for me.

Anyone here see any problem running this processor/board combo with Ubuntu server 64 bit?

Anything I need to know?

Thanks

Bob

---

### Post by tgalati4 on 2009-12-20
It'll run fast.

---

### Post by holastickboy on 2009-12-20
A computer like that could divide by zero...

---

### Post by munky99999 on 2009-12-20
A computer like that could render a square triangle.

---

### Post by Skidbladniir on 2009-12-20
A computer like that could handle [http://roblox.com/](http://roblox.com/) * 500.  0_0

---

### Post by joker535 on 2009-12-21
Anyone with a useful opinion?


Is there something wrong with building a decent machine to host virtuals to test things before deployment?

What am I missing here?

---

### Post by joker535 on 2009-12-21
> **tgalati4 said:**
> It'll run fast.

I would hope so. My current one is fast but just not big enough to run more than 3 virtuals plus the host concurrently. Its a Dell 670 dual 3.2Ghz xeon HT box with 4G and Ubuntu 9.10 64 bit. It runs fine until I fire the 3rd virtual off and then it just runs out of ***. LOL

Thanks

Bob

---

### Post by BkkBonanza on 2009-12-21
If you want to run many VMs then how many you can run depends mostly on what they're doing and how much ram allocated/available. If they're just sitting idle and ram is enough you should be able to have lots. If they are very busy then faster hardware will obviously help.

If you're having trouble with this on VirtualBox (which I think is great) then I'd have a look at a solution meant for running dozens of VMs on one machine at once. There are several but the one I've tried because free is OpenVPS. This is the open source version of Virtuozzo and is used to run hosting solutions all over the web.

---

### Post by tgalati4 on 2009-12-21
The reason you are not getting helpful answers is because you are proposing something that should work out-of-the-box, with decent performance.

You could try running Xen since it uses less resources (RAM and processes ID's) since it runs a single kernel with multiple init instances.  Normal VM's are running multiple kernels (one for each instance) and this uses up a lot of RAM and can use up CPU cycles.

"I'm thinking of taking a trip across country.  I'm torn between renting an older ferrari or a lambo.  Any opinions?"

---

### Post by munky99999 on 2009-12-21
> **tgalati4 said:**
> 
"I'm thinking of taking a trip across country.  I'm torn between renting an older ferrari or a lambo.  Any opinions?"
Hummer we need to burn fossil fuels faster in order to get global warming going faster. It's still wayyyy to cold in Canada.

---

### Post by Skidbladniir on 2009-12-22
> **munky99999 said:**
> Hummer we need to burn fossil fuels faster in order to get global warming going faster. It's still wayyyy to cold in Canada.
Yes, well it's wayyyy to hot in Texas.  It's 75 degrees in winter.  :P

---

