---
title: "Best option for a newbie?"
date: 2015-08-18
forum: Server Platforms
---

### Post by kim18 on 2015-08-18
Hi,

My friends and I are going to start a video site including several hundreds of videos, something like Youtube. We were looking for a [[COLOR=#000000]cheap web hosting[/COLOR]]("http://www.goldpuma.com") provider and after [[COLOR=#000000]comparing the reviews of top web hosting services like bluehost, hostgator and godaddy[/COLOR]]("http://www.threehosts.com") and using a [[COLOR=#000000]coupon from a website providing web hosting promo codes we chose bluehost[/COLOR]]("http://www.threehosts.com/reviews/1st") and set up our website with one of their Plus shared hosting package. Unfortunately, a few days later bluehost banned our account and told us we had to purchase one of their VPS or dedicated servers! This unprofessional behavior made us angry and we cancelled our account, because their dedicated servers are several times more expensive in compared to their shared accounts.

Now we have chosen a VPS account with Godaddy which is cheap, but since we don't have any experience with using VPS we don't know which OS is more preferred for us as newbies. Godaddy offers Ubuntu, CentOs and Fedora. Godaddy recommend CentOs 6 for beginners ([https://garage.godaddy.com/tech/config/how-to-choose-the-right-linux-distro](https://garage.godaddy.com/tech/config/how-to-choose-the-right-linux-distro)), but most users on different websites recommend Ubuntu! This has made me confused in choosing the right Linux OS.

Could you please advise me regarding the proper OS?

---

### Post by flaymond on 2015-08-18
Any Linux 'OS' will do, as long you know how to use the shell effectively, but I will personally avoid Fedora since the softwares will be updated frequently.


One of the starting tutorial to scripting on VPS - [https://www.digitalocean.com/community/tutorials/how-to-write-a-simple-shell-script-on-a-vps](https://www.digitalocean.com/community/tutorials/how-to-write-a-simple-shell-script-on-a-vps)

and you might not gonna see any GUI for the 'OS' you choose on VPS, since it's really for server, but I believe there's workaround somewhere.

So, of course, be familiar with the shell scripting, and you can do a lot on your VPS. Thanks.

---

### Post by nerdtron on 2015-08-18
Ubuntu is a good choice since you are already on this forums and people here can help you on your concerns. The operation of Apache/web service on CentOS is almost the same as that of Ubuntu with some differences like the default folders and vhost configuration folders.

---

### Post by mastablasta on 2015-08-19
first are you sure they were the ones who were unprofessional? users have to read ToS first. I never used them but I heard they are good host.

secondly, since you are newbie it doesn't really matter what OS. you will need to learn it anyway. CentOS and Ubuntu LTS are known for stability. Debian even more so (in my opinion debian is way too conservative for desktop but excellent platform for server).

you have a lot of learning ahead of you. if you need a GUI to help you manage the server I recommend Ajenti or Zentyal on Ubuntu. CentOS 6 - I am not sure if they support 6 or 5 but Nethserver and ClearOS are both good any newbie easy server interfaces. Ajenti works on CentOS as well. what I like about Ajenti is it's built in terminal and notepad for editing the config files.

learn also about SSH.

---

