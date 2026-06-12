---
title: "Advice on best security setup - usb drive os or virtual machine or other?"
date: 2008-07-27
forum: Security
---

### Post by jimmy the saint on 2008-07-27
I am toying with the idea of creating a secure system to use for online banking, personal finance software and some sensitive business related tasks.  I have a moderate level of computer skill, but I am certainly not pro-level or a linux guru.  My knowledge of information security is very limited... so please use small words!! 

I am considering two possible solutions, but I don't know which, if either, is the best.  First, I am considering installing an OS on a usb stick and encrypting it using the standard Ubuntu encryption software.  This seems ok, but the usb stick could easily be lost.

The second solution I have been considering is setting up a VirtualBox machine and installing an encrypted Ubuntu OS. 

Is there a better way that I have simply missed?  What are the ramifications of such solutions, and what are their shortcomings/limitations?

And before anyone points it out, I know that no security is foolproof, but I live in an apartment community that has a break in at least every week.  I would at least like to keep the data secure if some lowlife piece of... whatever steals my hardware.

Thanks for any input.

JTS

---

### Post by cyphercrypt on 2008-07-27
I think the easiest thing you could do is set up an encrypted volume and set it to mount to ~ for some secure user.

If you are worried about data leaking through some unknown manner, then you can instead have a regular virtual machine (not encrypted) saved to an encrypted volume.

I would personally go with the second option.

---

### Post by hyper_ch on 2008-07-28
another thing is to set your banks IP and domain in your hosts file so that now dns poisoning has an effect on you.

---

### Post by jimmy the saint on 2008-07-28
So would it be reasonable to place a VDI (VirtualBox machine) on an encrypted USB stick and run it from there?  Would this be a flawed strategy for any reason?  I figure that the advantage here is that it is portable. 

On another note, is there a fairly easy to understand primer on these aspects of data security options?  The only ones I have found are software specific, specific tutorials, or so complex they may as well be encrypted for all the good trying to read them does me!  

thanks

---

### Post by cyphercrypt on 2008-07-28
You should encrypt your swap, or just plain turn it off.

Moreover, there will be data leaks to at least /tmp and such. Not to mention the fact that virtual machines tend to save memory dumps. Depending how you have your vm configured it may leak data to the unencrypted portion of your disk.

If you want to be truly safe you should use full disk encryption. The performance penalty incurred is really not noticeable.

Also, you should read about DMA attacks. One paper in particular, Owned by an iPod, is quite frightening.

---

### Post by hyper_ch on 2008-07-29
> **cyphercrypt said:**
> If you want to be truly safe you should use full disk encryption. The performance penalty incurred is really not noticeable.

Well, it is noticable if you have large read/write operations... but for normal usage you shouldn't notice much of an impact.

---

