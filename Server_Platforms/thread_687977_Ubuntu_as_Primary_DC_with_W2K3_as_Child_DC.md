---
title: "Ubuntu as Primary DC with W2K3 as Child DC"
date: 2008-02-04
forum: Server Platforms
---

### Post by gairy_s on 2008-02-04
First I'd like to thank rickyjames for his tutorial for OpenLDAP + SAMBA DC
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Here is my problem. I have set up an account with DynDNS in order to access my server when I'm not at home. I could do this with the IP, but my wife is not that savvy, and I don't want her to have to keep remembering the IP address each time it changes.

Here is what I am looking for. I want to set up my Ubuntu server as the primary domain controller. With it I want to also host a private site with authentication. My logic behind this is to allow my wife to click a shortcut on her desktop (she uses Vista) and come to a page with a login somewhere. Once she is in, I want to set her as an limited admin and give her FTP access. This is due to the fact that she travels a lot for work and needs something like this on the road. For myself, I will set up the same and also set up a VPN for when I need it. I have 2 websites that I host on Linux servers, and I love the simplicity of setting up the sites and applying changes when I need to.

The next part is where my problem comes in. I have a 12 year old daughter who has missed school a few times because after we left for work, she played on the computer and missed the bus (her bus comes 1 hour after we leave for work). All 3 of us are in school, so unfortunately Windows is a necessary evil because for some reason, educational software picked by the various schools only run on Windows or Mac. I use a dual-boot, but this is not an option for my wife and daughter due to their limited computer skills. I have set firewall rules in the router and enabled passwords on everything, so that prevents some things, but not local gaming. If I use Win2K3, which I have an Enterprise copy from one of my courses, I can control her log-on times, and pretty much EVERYTHING she can do on her computer, which is running XP. 

I was thinking about running this as a child DC to the parent Ubuntu DC. When I start configuring everything, I'll use the Samba and OpenLDAP tutorial to work on getting everything to jive. The only reason for the W2K3 server will be for this and possibly some other things, but the Ubuntu server will remain my workhorse because I know it can handle it.

Does anyone have experience in a situation like this? Is there any advise as to whether this is a feasible solution? I know it may be a pain at first, but I have only taken the first courses for W2K3 server and SLES 9 server, so I really only know the basics on how to make them work. I'm also in school to become a network administrator, and I know this will help me get out of the “workgroup” mentality and force me to focus on the domain concept. 

Thank you in advance for your time. I have grown to love Ubuntu, and it is now the only OS on my laptop and my main OS on my desktop. The only reason I still have Vista installed is for Counter-Strike and school work, and when I replace my desktop for a better one, I plan on virtualizing XP to run those 2 and running MS out of my home life :). Thanks everyone.

---

