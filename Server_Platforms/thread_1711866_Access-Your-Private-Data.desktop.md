---
title: "Access-Your-Private-Data.desktop?"
date: 2011-03-21
forum: Server Platforms
---

### Post by HalbergM on 2011-03-21
Preface:
[I]I tried the search function and it didn't seem to return any results that I needed, and I apologize in advance if there is a thread I over looked that is pertaining to the same issue. 

[/I]Here's my issue:
Today my ubuntu server (10.10) started giving me issues with 'segmented  argument' when I attempted to use a sudo command. I tried a system  recovery and two issues have arisen.

1) during reboot the system says 'The disk drive for  /dev/mapper/minecrack-swap_1 is not ready or not present' and it just  hangs up on there. it gives me the options to skip or a manual recovery

2) It moved all my data into a Access-Your-Private-Data.desktop file  that is in my home/mark/ directory which I cannot access no matter what I  try.

I am using this server as a game server and all I care about is my need to get it the  level information off of it, and storing it on my website for the time being so I may put it back when I get it fixed. Then I have no problem reformatting  everything because I have not started to use the machine for anything I  intended it for.

Thanks for any help!
Mark

---

### Post by garfonzo on 2011-03-22
I would boot from a LiveCD, say Ubuntu desktop LiveCD, then you should be able to access all your information. From the LiveCD you could transfer your data off your server to your website for the time being, and then do a clean install of Ubuntu Server. I've run into situations like this where I can't boot the system to retrieve data. My solution is always to boot from a LiveCD.

---

### Post by HalbergM on 2011-03-22
garfonzo, thank you kindly for the reply.

However, I must apologies for my ignorance. When I burn the image of Ubuntu Desktop (64bit) to a CD and place it into the CD drive of my server, it give me the option to install ubuntu server. I am confused as to why I am not seeing anything about the desktop version. I confirmed that the disk was properly burned, not just a data CD with the .iso file on it, but the image itself was used to create the CD so it has all the directories it should have.

I am able to stumble my way through the setup menus and run a shell to get to a command prompt (a gray background and black text, unlike the usual black background and white text), but from there I am lost. I tried researching how to mount the /usr data but that was to no avail. 

I am relativly new to Linux, and have self taught myself up until this point. besides getting files onto the server from an FTP, and setting up and running the game's server, I am sadly rather lost in the dark.

Thanks.

---

