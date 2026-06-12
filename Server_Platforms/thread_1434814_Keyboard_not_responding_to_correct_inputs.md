---
title: "Keyboard not responding to correct inputs"
date: 2010-03-20
forum: Server Platforms
---

### Post by whipp3t on 2010-03-20
Hi I am new to the server platform, I have installed it correctly and I am currently trying to configure my sever network etc......


I am running this server on a dell D - E520 which needs a USB keyboard, as there is no PS2 inputs.

When I install the server, and get it to the running page, and I want to create a static address for networking, my keyboard keys does not work correctly as they should. I can manage to get to open the network interfaces file but trying to edit it is a nightmare.

I press the insert key so I can edit, but it doesnt work, all the keys are doing different things. The backspace key isnt working like it should, and also the insert key. When I press the ENTER key it does notting, when I press the backspace key it decides to bring the cursor over to the left, as if I were pressing the left arrow key etc....

When I was pretesting it in VMware, it worked perfectly, but not with a stand alone machine which is stated above, 

Has anyone every come accross this problem before ? and if you have, can you shed some light on the matter.

I've reinstalled a few times with different keyboard configs for different countries, USA, IRE, and UK but still all the same.
regards

---

### Post by KB1JWQ on 2010-03-23
What text editor are you using?

Does the keyboard work properly in bash?  How about in nano?  What about vim?

---

### Post by whipp3t on 2010-03-23
> **KB1JWQ said:**
> What text editor are you using?

Does the keyboard work properly in bash?  How about in nano?  What about vim?

Hi there, 

Thanks for getting back to me, to be honest, I haven't even tried the other editors as I was reading a tutorial I got from these forums and google, and they were using the vim editor. This was the editor I was using with no problems in VMware. 

I didn't know that the ubuntu server came with those different editor's, I will try these out and report to you later. 

Thanks once again for your help buddy :D

---

### Post by jsprev on 2010-03-24
> **whipp3t said:**
> Hi there, 

Thanks for getting back to me, to be honest, I haven't even tried the other editors as I was reading a tutorial I got from these forums and google, and they were using the vim editor. This was the editor I was using with no problems in VMware. 

I didn't know that the ubuntu server came with those different editor's, I will try these out and report to you later. 

Thanks once again for your help buddy :D

I discovered that vi under Ubuntu acts that way - I had to install vim and that works wonderfully.  From my past experience I thought typing "vi" just brings up vim but that doesn't appear to be the case here where they maintain the difference.

---

### Post by KB1JWQ on 2010-03-24
Yeah, it's a known keybinding issue.  vim versus vi has these results for me on FreeBSD.

---

### Post by whipp3t on 2010-06-19
Thanks to everyone for your replies.

Nano works right out of the box for me with no problems.

---

