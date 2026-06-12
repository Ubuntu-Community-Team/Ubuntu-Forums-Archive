---
title: "Ubuntu + Samba4 &lt;=&gt; Exchange server ?"
date: 2014-09-23
forum: Server Platforms
---

### Post by Trung_Huynh on 2014-09-23
Hi everyone , I'm new to ubuntu server and samba.

My company is using Windows Small Business Server (SBS) 2008 which only allow to create maximum 75 users ( also 75 exchange mailboxes). Windows SBS is using as DC server and Exchange server. All of user desktops is Windows (XP & 7).

Here is the situation: the number of users is continue to grow to more than 75 (we need a lot of data entries, only a few of team leaders). We are planning to have more than 100 users of data entry level and 30 users of management and leader level. So we need to find a economic solution for total 130 domain users in the future. (we're not prefer to purchase Windows Server license and CALs for 130 users + printers and devices which will cost a lot of $)
One important note is: all data entries don't need to use email, only managers and leaders need to use email (and we're using exchange mail for its features: webmail, calendar, mobile...).

My first solution is to switch completely to Linux servers (for DC server and mail server). Ubuntu Sever is one great candidate that I'm considering. I will install samba4 on Ubuntu sever to make it as active directory DC and I'm considering for a linux base email server such as Zimbra or Sogo.
But for the 1st solution we must drop the Windows SBS with 75 exchange mail boxes (such a big waste!)

So my second solution is to install samba4 on ubuntu server to make it as active directory DC for 130 domain users , but still keep SBS as Exchange server for 30 users that need to use email.

So my question is how to make Exchange server communicate with Ubuntu server and sync 30 users with 130 users from the Ubuntu server (the PDC) ? Is it possible? Or there is any other solution?
Does ubuntu server has similar policies with Windows Server?

Sorry for my English, it's not my native language.
Thanks in advance.

---

### Post by Michael_McKenney on 2014-09-23
I would discuss it with your management team and lay out the options.  I have 30+ years experience with corporate data centers.  I am the senior network engineer and run a corporate data center.  We are 100% Microsoft.  We have SQL, Exchange, etc.   In a production environment, you want reliability and performance.   You being new to Ubuntu means switching from Microsoft will not give reliability and performance.  The costs for Linux Enterprise vs. Microsoft is very similar.  I love my Ubuntu boxes at home.   I would not bring Ubuntu or Linux into our network without the network team being fully trained on it first.  Uptime is important.  Microsoft Exchange works best in a Microsoft environment.    My CFO and I consider Linux Enterprise for our web services.  We decided to have the web site hosted instead.  If you want to switch to Ubuntu enterprise for the corporate environment, I suggest hiring a consultant and taking classes to learn how to use it first.   You need to talk to management first and find out if Linux is even an option.  None of our vendors even write for Linux or Novell any more.  They are only Microsoft.   So you need to check with your software vendors too.

---

### Post by lingpanda on 2014-09-23
> **Trung_Huynh said:**
> Hi everyone , I'm new to ubuntu server and samba.

My company is using Windows Small Business Server (SBS) 2008 which only allow to create maximum 75 users ( also 75 exchange mailboxes). Windows SBS is using as DC server and Exchange server. All of user desktops is Windows (XP & 7).

Here is the situation: the number of users is continue to grow to more than 75 (we need a lot of data entries, only a few of team leaders). We are planning to have more than 100 users of data entry level and 30 users of management and leader level. So we need to find a economic solution for total 130 domain users in the future. (we're not prefer to purchase Windows Server license and CALs for 130 users + printers and devices which will cost a lot of $)
One important note is: all data entries don't need to use email, only managers and leaders need to use email (and we're using exchange mail for its features: webmail, calendar, mobile...).

My first solution is to switch completely to Linux servers (for DC server and mail server). Ubuntu Sever is one great candidate that I'm considering. I will install samba4 on Ubuntu sever to make it as active directory DC and I'm considering for a linux base email server such as Zimbra or Sogo.
But for the 1st solution we must drop the Windows SBS with 75 exchange mail boxes (such a big waste!)

So my second solution is to install samba4 on ubuntu server to make it as active directory DC for 130 domain users , but still keep SBS as Exchange server for 30 users that need to use email.

So my question is how to make Exchange server communicate with Ubuntu server and sync 30 users with 130 users from the Ubuntu server (the PDC) ? Is it possible? Or there is any other solution?
Does ubuntu server has similar policies with Windows Server?

Sorry for my English, it's not my native language.
Thanks in advance.

I would start by testing samba4 on a VM or test box. Start learning it before you introduce it into a production environment. I currently have 7 Samba4 DC's across several sites along with Squirrelmail as my exchange alternative. I have a Kolab server in a test phase now that will replace my Squirrelmail box. I have 120+ users and 140+ workstations and servers. It's nice not having to deal with CAL's. All this freedom does come with a price. YOU must know how to support these machines or look to pay someone if things go wrong. Samba4 does offer commercial support I believe. With all that being said. I'm not sure if samba supports joining a SBS to it. Take a read through this post where someoine has tried to do what you are currently looking into. [https://lists.samba.org/archive/samba/2014-January/178358.html](https://lists.samba.org/archive/samba/2014-January/178358.html) Good luck!

---

