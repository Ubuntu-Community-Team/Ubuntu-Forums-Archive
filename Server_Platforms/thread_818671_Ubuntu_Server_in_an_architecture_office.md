---
title: "Ubuntu Server in an architecture office?"
date: 2008-06-04
forum: Server Platforms
---

### Post by dabarron on 2008-06-04
Hello Everyone,

We are currently looking into buying a server station for our 6 person firm. This 6 will eventually expand to 10. We our outgrowing our current setup. Our current setup consist of one Windows XP Home station that acts as a server with file sharing. We have a file structure that holds all of our AutoCad dwg files, images, documents, etc. Then the other xp stations access this computer. As you may know the XP Home has a session connection limit of 5 and XP Pro is 10. 

We looked into a Dell Server with a Windows Small Business Server, but with CALS and everything else it was getting into the 3000 dollar range. I was finding the CALS ridiculous. A small Business Server comes with 5 CALS. That is basically a glorified XP Home. Buy a pack of 5 more CALS and you have a glorified XP Pro machine. Then I thought, I have been hearing so many great things about ubuntu let me take a look at it. 

However, I have a problem that I am not sure about since our office revolves around the use of AutoCad. We run AutoCad on our individual workstations, which is fine. We wouldn't have a need to run Autocad on a Ubuntu Server. However, we would store and access the .dwg files on the Ubuntu Server. 

At one time we purchased a Buffalo Technology TeraServer and moved all our files over to it. We ran into a big problem. Accessing the Teraserver with Autocad on a windows machine, we could open the .dwg files on the TeraServer but we could not save back to the TeraServer. My research at the time showed that when a save was taking place the .dwg file could not find certain API's (I think that is what it was called) to complete the operation. I was told that Autocad .dwg files could only be stored and supported on a windows operating system/server. 

I am hoping that this is not true with an Ubuntu Server. Is it possible to have AutoCad on our individual window workstations and be able to fully access our .dwg files stored on an Ubuntu Server with no problem? Anyone have any first hand experience in this?

One quick question to end, are you able to set up a mail server on the Ubuntu Server that will work with Outlook in sharing email folders, contacts, etc.?

Thank you for your time and your suggestions.

---

### Post by quelx on 2008-06-04
It shouldn't be to difficult (I'd say an hour or two at most) to setup Ubuntu desktop (go ahead and use the GUI since this won't be in production) or even the Live CD itself with **samba** and try opening a .*dwg*, then save it back to it and see what happens.

[https://help.ubuntu.com/community/SettingUpSamba#head-9a5351db3adc7d5fda5f639903169fc5d185f297](https://help.ubuntu.com/community/SettingUpSamba#head-9a5351db3adc7d5fda5f639903169fc5d185f297)

This isn't an answer to your question, and for that I apologize :) .

---

### Post by freebeer on 2008-06-04
I've certainly opened .dwg from Ubuntu (but not in AutoCad).  I'm pretty sure I've saved them back directly, too.

Assuming there's something in AutoCad that won't permit a direct read/write (and I can't imagine that being the case), you can always save locally, then copy it over.  This can be automated, of course.

You're right about the CALs.. it's a ridiculous price to pay for additional users.  That's why I've moved over to Ubuntu for my storage needs.

---

### Post by gtdaqua on 2008-06-05
> 
One quick question to end, are you able to set up a mail server on the Ubuntu Server that will work with Outlook in sharing email folders, contacts, etc.?


Try [Zimbra]("http://www.zimbra.com/"). There is a free edition and this is actually a great Colloboration Suite. 

Storage performance in my opinion is better in Linux-based OS than Windows especially because of Linux's superior ext3 filesystem. Your setup seems simple and Ubuntu could easily work out for you.

---

### Post by dmizer on 2008-06-05
about 2 1/2 years ago, i built an ubuntu server which hosts cad .dwg files and it's had no issues that i can recall.  in fact, that server is still active and serving a cad computer as i type this message.  don't know why anyone would think that .dwg files would be any different than any other file.

a few words of advice:
ubuntu is probably more OS than you'll ever need for a file server.  i suggest something like freenas: [http://www.freenas.org/](http://www.freenas.org/) which has a browser interface for configuration, and is really quite powerful.

never allow external access to a computer which stores business critical files.  or in other words, if you want a mail server (which ubuntu is perfectly capable of), do not have your email server on the same computer as your shares.  email servers are targets.  you're better off keeping your sensitive files as isolated as possible.

also, if you do go with ubuntu, be sure to install an LTS server version.  it will save you hours of upgrade headaches every 6 months.

---

### Post by dabarron on 2008-06-11
Thank you everyone for the suggestions. Hearing what everyone is saying is giving me a lot of hope. 

@quelx: I downloaded the desktop version and started up from the cd. I also used the link you gave me. I could see the windows computers in ubuntu but each workgroup computer was empty or didn't show anything when I clicked on them. I wasn't able to connect to ubuntu from a windows computer. I think I need to have ubuntu installed on the system to really get it working. Does this sound right to you? I just need to find a workstation that I can fully test this on. As usual, IT budgets are so tight I don't have this luxury. I may have to bring in my mac from home and test this. 

Thank you again for everyone's insight. If anyone else has any thoughts, I would love to hear them.

---

### Post by quelx on 2008-06-11
> **dabarron said:**
> 
@quelx: I downloaded the desktop version and started up from the cd. I also used the link you gave me. I could see the windows computers in ubuntu but each workgroup computer was empty or didn't show anything when I clicked on them. I wasn't able to connect to ubuntu from a windows computer. I think I need to have ubuntu installed on the system to really get it working. Does this sound right to you? I just need to find a workstation that I can fully test this on. As usual, IT budgets are so tight I don't have this luxury. I may have to bring in my mac from home and test this. 


You ought (I've done it for other network services from a live CD, but never samba) to be able to:```
sudo apt-get install samba
``` create a read write share:
*/etc/samba/smb.conf*```
[test]
        browsable = yes
        path = /home
        public = yes
        writable = yes
        guest ok = yes
```
```
sudo chmod -R 777 /home
```(of course you would never do this on a real system , but a live CD, meh)
restart samba
```
sudo /etc/init.d/samba restart
```
get the ip address of your live environment (**ifconfig**) and on a windows machine **Start** > **Run** > **//192.168.1.20/test**

If you can open it, throw a dwg file in it (a small one, since it's running on a RAM disk) open AutoCAD, open the file, make a small change save it back.  If it works, great.  If not double check my example *smb.conf* and make sure there is enough RAM disk available for the dwg file you are trying to move over.

---

### Post by molotov00 on 2008-06-11
I agree that I would not put email on the same server as .dwgs.

What you are asking to do with this server is CERTAINLY not worth paying $3,000 for. Your file sharing requirements are very basic and most home users of Ubuntu have that functionality. Ubuntu also allows you to set up some more advanced file permission options (i.e. if you have a secretary you can exclude him/her from accessing the files). As you probably know, you can't do that in XP Home.

You haven't mentioned backups of any kind. If you are using tape drives then that's something most users of this forum won't know much about.

If you do want mail on the same server, again, that's something most hobbyists won't know much about.

If I were you, I'd talk to Canonical about your needs. Get them to commit that it will meet your needs. Pay a little for the support if you aren't comfortable with Ubuntu. Being that it is mission critical, I'd get Canonical behind me.

Your needs are basic though. Ubuntu could definitely work. It's more about your comfort level with trying something new.

---

### Post by andguent on 2008-06-12
I read down the thread and at each post I was nodding my head in agreement. I have partially been involved with the setup of 40-50 Linux file servers (not to brag, just quantifying knowledge level). 

I actually have seen one example where a Linux server didn't quite suit for a file server. Quickbooks Multi User Edition (multiple people signed in at once) requires an agent (windows software) run on the file server and babysit the connections. This is not needed if none of the Quickbook files are used by multiple people at the same time. With previous versions this was not an issue either. As of 2007 or so it was introduced, and with much resistance.

My expectation for AutoCAD files is the same. If only one person is using the .dwg file at a time, AutoCAD shouldn't even know/care what OS it is saving the file to. I'm not aware of AutoCAD being able to have two people open the same data file, but I've been wrong before.

Separate servers for email & internal files: Agreed, done right it really should be a separate firewall DMZ area, with the LAN protected from it. It is very complicated to host your own email server internally.

Zimbra: Zimbra is very impressive, especially for small businesses that want to share calendars. Calendar/Contact integration with Outlook costs money, but it is extremely well done. The syncing is better then any other sync software I have seen for Outlook (with the exception of Exchange of course). See above note about DMZ.

Another email option to simply be aware of is Google Apps. If you can handle GMail style ads (text, not annoying), then you can use that for free with your own domain. Shared Calendars & Contacts are dead easy to setup (probably automatic by default). You always have remote access into your email, as it is hosted at Google anyway. To loose the ads and get official Google support requires $50/yr/user, or "Charitable non-profit" status.

Consultants/Support: Make sure you have official support as an option somewhere from someone, unless you can handle a day or two of downtime while you learn something new. This really is true no matter what operating system you use.

In short, get a generic white box PC with name brand equipment, and two hard drives. Use RAID mirroring (not really easy for a beginner, but very worth it) and sleep easy. Total hardware cost should be $500-$600 US.

---

### Post by deecee52 on 2008-06-12
Whether you can successfully use autocad on a linux server, depends on what flavor of autocad you are using.  We switched from a simple peer to peer file sharing system for ADT 2000i to a linux based NAS raid system and all was fine.  However, when the adt 2005 files and the  project navigator protocol was completely realized, things began to break.  You cannot create a project on a linux server.  The .apj file will not be created in a way that is recognized as a project by autocad. Additionally we had to a create a common user so that the various xrefs and such were not locked  and unavailable for another user.

 I don't know if that has been corrected in architecture 2009 (sitting in box, yet to be loaded 'cause old projects still active with consultants, and new projects being started in revit).

Revit, although it has some of the same permissions issues, is by nature a single user process.  You borrow aspects of the drawing - and it recognizes that you may be an engineer, an architect, in this office or another -- and then you return it to the master drawing.

This was a long way to say that it can be done, but you will not get any help from autodesk as they are totally wedded and in bed with M$.  Remember, autodesk doesn't even run on macs.

We have been using Thunderbird and lightening internally using ubuntu server for the imap and ldap servers.  I've also installed horde to allow web access to calendars as and mail. It's not particularly elegant, but it has allowed our windows boxes to lose some of the M$ bloat and just focus on the few proprietary aps we really need.

---

### Post by molotov00 on 2008-06-13
> **deecee52 said:**
> The .apj file will not be created in a way that is recognized as a project by autocad.

That doesn't make any sense to me. As far as the client is concerned the server is "Windows". You could even use an NTFS partition if you wanted to.

As far as permissions go, you can set up the Linux server with whatever permissions you want.

I don't really understand how this situation is possible.

---

### Post by dabarron on 2008-06-13
@quelx: thank you for the code and hints. I was wondering how ubuntu was working when you used the live CD...ram. 

@molotov00: I was hoping our needs were basic. As for a backup system I have a Maxtor 200gb drive that goes through an automatic backup every evening. So I would place that drive with the server setup. I have had my experience with tape drives and it was a nightmare to say the least. We would definitely use the file permissions for accounting, HR and such that others in the office have no need to access. Since we will be moving from peer to peer, to the possibility of ubuntu, it would be nice to install a database driven timesheet application, etc, etc. However, our needs are still basic at the moment. 

@andguent: A total hardware cost of 500-600 would make me look like a hero. My main profession is architecture, but with my knowledge of I.T. I have been very resourceful in the office infrastructure and budget. Currently our mail server "so to speak" is gmail. I have it going through gmail before it comes to us. This has reduced spam by 95% or more. And as you mentioned, everyone can check their mail outside the office. It gives us an online backup as well. Never fails, "I can't find a message, I think I deleted it five weeks ago, can you recover it." Right on money about the Raid. My specs was certainly going to include this. 

@deecee52: You bring back memories of the exact problem I was having with the terra server. I couldn't get a straight answer from anyone. The person that told me that it is not supported on non-windows servers was an autodesk reseller. He said exactly what you said, autodesk will not support anything else but window servers. We currently have one machine on 2000 and the rest run 2005. We are in the market as well for the latest version which I wish was revit but I know will be just autocad. Currently we use plaxo to share contacts, calenders, and tasks. It works, but I am seeing its limits the more we grow. We have nothing yet for a central sharing of email. 

Thanks again everyone, I must get back to work even on a Friday.

---

### Post by deecee52 on 2008-06-13
> **molotov00 said:**
> That doesn't make any sense to me. As far as the client is concerned the server is "Windows". You could even use an NTFS partition if you wanted to.

As far as permissions go, you can set up the Linux server with whatever permissions you want.

I don't really understand how this situation is possible.

I agree with you, I don't understand how this is possible, but infact it is.  If you look on the autodesk forums, you will see several references to the problem on creating the .apj files if you are using the autodesk sheet and project navigator features in ADT 2005 and later. I do not know if the problem has been fixed in the newer versions.  There were work arounds, but it involved creating the project locally and then saving the set back to the server and remapping the project.

Both the Owner and the group had to be same.  Evidently ADT does not release the ownership of the files.  This was on a samba server.

There are many questions on both the autodesk discussion group and the augi forums., but no definitive solutions. There are several references that this has to do with "sticky bits", but again there have been no definitive solutions to the problem.

If you don't use the xref and object oriented features of the software, you can save the files to the server, but then it's just not worth it.

---

### Post by MrkCrwly on 2008-07-03
Sorry to butt in but I bring good news:
We have a Archtecture/Engineering office with about 15 people and use AutoCAD Architecture 2009 and AutoCAD Civil 3D.
Per this thread we did a quick Ubuntu Desktop setup on a spare Dell computer as a test.
So far we do not notice any differences between using Ubuntu for a file server and SBS2000.  All tests have been with Arch 2009 both with and without using the Project Navagator.  We had no file locking issues between users.  In fact we had no issues with XP finding and using Ubuntu.
Looks like we will try and setup Ubuntu Server and see if we can use that for our server instead of upgrading to SBS 2008.
Thanks
Mrk

---

### Post by deecee52 on 2008-07-04
> **MrkCrwly said:**
> Sorry to butt in but I bring good news:
We have a Archtecture/Engineering office with about 15 people and use AutoCAD Architecture 2009 and AutoCAD Civil 3D.
Per this thread we did a quick Ubuntu Desktop setup on a spare Dell computer as a test.
So far we do not notice any differences between using Ubuntu for a file server and SBS2000.  All tests have been with Arch 2009 both with and without using the Project Navagator.  We had no file locking issues between users.  In fact we had no issues with XP finding and using Ubuntu.
Looks like we will try and setup Ubuntu Server and see if we can use that for our server instead of upgrading to SBS 2008.
Thanks
Mrk

Good news is never an intrusion.  I'm glad to hear Architecture 2009 works with the server.  We are currently using a linux nas as a file server - and as I said it works fine for everything inlcuding Revit 8, except ADT 2005.

The NAS backs up to a usb drive and to a ubuntu server.  The ubuntu server does email and calendar.  This has the added advantage that my files are not exposed to the web -- all of that is handled by the Ubuntu Server.  Samba server works just fine and no other specialty apps like adobe or corel had any trouble with the set-up.

---

### Post by Wharf Rat on 2008-07-04
dabarron,
Do yourself and your firm a huge favor and look at a commercial server.  Ubuntu, and most linux distros, can act as a server if set up properly.   Not trying to be rude with this statement, but if you had the expertise to set up a linux server using opensource products, I doubt you would have posted the original question.

Having said that,  I do think linux is the way to go.  I have used a linux server for about 10 years on a small net.  Four years ago I installed a Nitix server -- solid as granite.  It is VERY easy to configure - as it does most of the work for you. 
I talks to almost all other OS's, has firewall, web, mail, services and has a product called ExchangeIt that mimics a Microsoft Exchange server.  We use Outlook on all the workstations and have shared information that is transparent to the user.  And last, but far from least, it has excellent backup software built in to the system that uses a removable drive.  Just swap drives on a regular schedule and you are home free.  Restore controls use a web interface for the Admin.

[www.nitix.com](www.nitix.com)   now a division of IBM.

The initial cost will be close to that of a MS Exchange sytem.  I think we paid about for $4000 for our second unit with Cals for 16.

---

