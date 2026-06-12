---
title: "EMERGENCY! Help![Solved]"
date: 2007-12-08
forum: The Cafe
---

### Post by Method9455 on 2007-12-08
Hi all,

I'm at a hospital with a family member and my Ubuntu laptop. I need to get into a website for some information, but I don't have the password, and the owner of the site doesn't read his email often enough to get back in time. I know the site is accessible from my Ubuntu desktop at school, because it is on the college network. The network is closed from the outside. My desktop at school is on and I have an SSH server opened and connected. I know the address of the site I need. How do I navigate to the page and read it through the command line? I have wget but that just downloads right? I know how to open X windows servers through ssh, but can I just open firefox and tunnel it through SSH or do I need to use an X specific utility? Is there something that will print a website to the command line like cat? I just need the text not the pictures.

Thanks, help would be greatly appreciated. Got to love when Linux is actually saving our *** doing something windows can't, I knew there was a reason I switched.

---

### Post by zachtib on 2007-12-08
> **Method9455 said:**
> Hi all,

I'm at a hospital with a family member and my Ubuntu laptop. I need to get into a website for some information, but I don't have the password, and the owner of the site doesn't read his email often enough to get back in time. I know the site is accessible from my Ubuntu desktop at school, because it is on the college network. The network is closed from the outside. My desktop at school is on and I have an SSH server opened and connected. I know the address of the site I need. How do I navigate to the page and read it through the command line? I have wget but that just downloads right? I know how to open X windows servers through ssh, but can I just open firefox and tunnel it through SSH or do I need to use an X specific utility? Is there something that will print a website to the command line like cat? I just need the text not the pictures.

Thanks, help would be greatly appreciated. Got to love when Linux is actually saving our *** doing something windows can't, I knew there was a reason I switched.

try logging in like this:

```
ssh -X address_of_server
```

to enable X forwarding, and then just try and run firefox.... it'll be really slow, but should work

---

### Post by p_quarles on 2007-12-08
Two options:

1) Lynx. It's a barebones, ncurses based browser. Won't read all sites, but it's the first thing to try:
```
sudo apt-get install lynx
```
2) Download the entire site using wget, and then transfer it to your laptop. This method won't work with all sites either.

Past that, there's X forwarding, which will take a bit more setup.

---

### Post by Method9455 on 2007-12-08
thanks guys, I tried ssh -X (my comp) firefox and it didn't tunnel, but then I tried Lynx and that worked out you guys are awesome. i owe you

---

### Post by zachtib on 2007-12-08
> **Method9455 said:**
> thanks guys, I tried ssh -X (my comp) firefox and it didn't tunnel, but then I tried Lynx and that worked out you guys are awesome. i owe you

well, you'd have to log into the box first, and then start firefox,

but i'm glad you got it working :)

---

### Post by bimmerd00d on 2007-12-09
> **zachtib said:**
> well, you'd have to log into the box first, and then start firefox,

but i'm glad you got it working :)

i think he'd need to make sure X11 forwarding was enable on both sides.  Glad it's all working, I was going to suggest lynx.

---

