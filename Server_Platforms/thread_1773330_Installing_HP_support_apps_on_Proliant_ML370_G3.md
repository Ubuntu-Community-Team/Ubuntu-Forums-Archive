---
title: "Installing HP support apps on Proliant ML370 G3"
date: 2011-06-01
forum: Server Platforms
---

### Post by competentfake on 2011-06-01
I've been trying for three days to figure this out, but I have to give up and ask for help.  I acquired an old ML370 Proliant server, and I'm attempting to find a way to control the fan speed, as all three noisy fans are running at full blast, and I had planned to keep this thing in the office, because it has no wireless capability or support.  

I know the following:
HP has a suite of programs that are variously called Insight Control Manager, Server Health driver, HP-health, hpasm, and a few more I can't remember.  Obviously these are different iterations of the same program, but I have been unable to determine which one I need, and I've been completely unable to find a way to install any of them or find the repository that contains them.

The website: [Download Drivers and Software]("http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?lang=en&cc=us&prodNameId=3279715&taskId=135&prodTypeId=15351&prodSeriesId=316541&lang=en&cc=us")
It lists a lot of different Enterprise-class Server OSes, but nothing about Ubuntu or any home server OSes.  I've only been at this for a week, so I don't know which of these would work with Ubuntu Server, or how to make them work if their aptitude file extension is not .deb.  I'm currently running Server version 10.10, as 11.04 gave me monitor troubles.  

I hope someone can help me, otherwise I'm going to have to buy a really long CAT-5 cable and stick this thing in the basement.

---

### Post by competentfake on 2011-06-02
I saw no rule against bumping on the CoC, and my post from 9 hours ago is like on page 16 of the new posts.  Still hoping someone can help.  :)

---

### Post by freechelmi on 2011-07-12
> **competentfake said:**
> I saw no rule against bumping on the CoC, and my post from 9 hours ago is like on page 16 of the new posts.  Still hoping someone can help.  :)

Hi I'm in the same problem with a proliant ML110 G6 ; 

I downloaded the RedHat 6 rpm and converted tham using "alien --scripts" on my 10.04 server ( 32 bits) 

then installed the deb which seemed to work as the script in the init.d are there.

Launch the two HP services but then I don't know how to tell the service to slow down the Fan ....

---

