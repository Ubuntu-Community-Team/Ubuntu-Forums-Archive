---
title: "How would you run Ubuntu 10.4 server and OSX 10.6 Server?"
date: 2010-10-18
forum: Server Platforms
---

### Post by 1serveyou on 2010-10-18
I would like to first start out and say this is for a home project, and not for a business/company. I have an older Mac Pro - 06-07, and trying to figure out the best way to run both. I've setup Ubuntu Servers before(I'm no expert, but no enough to be dangerous), and would like to use the OSX as more of a test server since all my data is ready for Ubuntu. I don't have a problem using command line for Ubuntu, but not too sure with OSX, and kind of like it's GUI(I know, shoot me haha). I tried to install(through SSH, as it is a headless server) Mac OSX server through VirtualBox on my Ubuntu 10.4 server, but it said that I didn't have X11 install so I couldn't use it. When I looked up X11, it seemed it was not encouraged to use X11 on a server. 

I did try installing Ubuntu with VirtualBox on the Mac OSX server which worked, but I've never used a virtual server before so it was tough trying to configure everything. Also with the Mac OSX server only being a test/practice server(I do have a few macs in my house), I rather have the Ubuntu get more ram/processor power.

Is anyone else doing something like this? Any help would greatly be appreciated.

---

### Post by arrrghhh on 2010-10-18
So you want to run both OSes at the same time... on the same hardware?  The only way to do this is virtualization, whether you go bare metal (like ESX) or guest/host (like VirtualBox)

If you want to run one or the other, you should be able to install a dual-boot setup - just make sure OSX is installed first.

---

### Post by 1serveyou on 2010-10-18
> **arrrghhh said:**
> So you want to run both OSes at the same time... on the same hardware?  The only way to do this is virtualization, whether you go bare metal (like ESX) or guest/host (like VirtualBox)

If you want to run one or the other, you should be able to install a dual-boot setup - just make sure OSX is installed first.

I'd prefer Virtual, as for now(and probably for awhile), the ubuntu server will be my main one, so if I dual booted, I wouldn't have access to my ubuntu server when using my mac osx. The problem being, I'm going to try to keep my client computers on the light side, and using the server as the main access point for information.

Which would you recommend, bare metal or guest/host? I'm a beginner when it comes to virtualization remember :P

Would it be better for me to list what I plan for the servers to be doing?

---

### Post by arrrghhh on 2010-10-18
Well bare metal you're going to get much better performance on both machines - but you'll still need pretty beefy specs to run two OSes at the same time.

Guest/host, both are going to kinda drag unless you have very good specs.

Both options would be benefitted from a chip that supports virtualization (AMD & Intel both have architectures that support virtualization).

I'm not aware of any 'free' (in every sense of the word) bare-metal virtualization platform.  ESX is great, and I *think* you can run it as long as it's for personal use.  Not sure on that, you'll have to do some research there.

Guest/host is probably the easiest to setup/configure/understand.  Bare-metal you'll get better performance and options IMHO.

---

