---
title: "Network Questions... Cloning Computers, Multicasting, Etc."
date: 2009-03-25
forum: The Cafe
---

### Post by Roasted on 2009-03-25
Here's my setup:

Dell Precision M4300 Core 2 Duo laptop, 2gb RAM, Ubuntu 8.10, FOG 0.26, 1x 10/100/100 ethernet port.

FOG 0.26 = Open Source Cloning Software, like Ghost, but free. :) 

I have a Dell 2724 PowerConnect switch with 10/100/1000 ports, along with 10 Lenovo R500 laptops to image which these Lenovo's also have gig ports on the ethernet, so essentially everything is 1000 heree. I have the image uploaded to my "server", the M4300 laptop with Ubuntu.

When I deploy the image to 1 laptop at a time, I can push it (18 gig image) in 15 minutes flat. When I deploy it via multicast to all 10 laptops, it rates an estimated time of 8 hours and 12 minutes to go, a direct indication it's pushing the images out via unicast.

I tried to look in the user interface of the switch to see if I could enable multicasting, but it doesn't seem that I can. I was reading on some other forums and people who were using Ghost were saying multicasting shouldn't matter.

Does anybody here know a lot about this kind of stuff? What exactly do I need to make my images kick out to these computers at a fast speed? I know it can be done, I worked at another district for an internship with Ghost that would push 15 images at once on a 16 port 3Com switch via multicast.

---

