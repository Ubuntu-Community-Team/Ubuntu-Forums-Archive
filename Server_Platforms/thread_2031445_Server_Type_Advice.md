---
title: "Server Type Advice"
date: 2012-07-22
forum: Server Platforms
---

### Post by Sketchies on 2012-07-22
Please, please forgive my lack of tech know-how in advance.  My  background is actually in animation, but I'm trying very hard to learn.

I  am a teacher at little school with no tech budget (aren't they all).  I  have a lab consisting of 25 Dell Hybrids, 4 MSI netbooks, and a custom  built server machine.  These machines are used by kindergarten through  eighth grade students.  My lab machines are currently being upgraded to  Edubuntu 12.04.  The issue is the server.  I'm not sure what type of  server to attempt to set up.

We have a closed classroom network with a line in from the ISP.  Its a gigabit network.

Here's what I really must be able to do:
1) Run Epoptes to monitor student activity, turn the machines off, and share my screen for examples.
2) Push updates and new software from the server to the lab machines (more of a want than a need).
3) Allow the lab machines to connect to the classroom printer connected to the server.

I  was planning on using the local guest user in 12.04 since it keeps  student damage to the machines at a minimum.  The hardware is old and  has taken a lot of abuse from outside sources.  Students are required to  have flashdrives to back up their work, plus I will have dropbox  available for them to store/turn in work.  I'm looking at implementing  Google Docs as well to avoid losing student work on the guest user.

Based on this information what type of server should I be looking at or do I even need a server?

Thank you very much in advance for any help.

---

### Post by kgatan on 2012-07-22
I have very limited experience with this, just done some testing in a home environment.

I would guess that the best option is to run all student clients as thin clients and use your workstation as a Edubuntu Server with LTSP.

This will give you better control to manage users, their files and monitoring.
Client management is done using the Edubunti Thin Client Manager (see below link)

Some information on Edubuntu server in this link,
[http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server.html)

From what i read a normal workstation with 3gb of ram can handle up to 25 clients so the requirements are low. 

Some pointers,
1. The clients need to be able to PXE-boot over the network.
2. The Edubuntu server needs its own DHCP for fast client deployment. Might be no problem but it depends if there already are existing DHCPs in your network.

(Edit: If your clients cant PXE-boot there are ways to get around it.)

---

### Post by Sketchies on 2012-07-23
We did try LTSP in the past with limited success.  However, its certainly worth trying again.  I'll update after I take another stab at it this weekend.  I will ask my network guy about the DHCP issue since I recall there being a red flag there.  Thank you so much for your help!

---

### Post by kgatan on 2012-07-23
I read some more regarding the setup of the LTSP enviroment.

You can avoid all DHCP problems by having two nics on the server machine. One acts as DHCP to a separate network for all the thin clients while the other nic is connected to your normal network.
I think that's the common setup for a "classroom".


I did a test in a virtual environment with Edubuntu 12.04 and it´s really easy to get everything working. More or less just point and click and your up and running.
For my small environment I have two issues that I would guess are important for a teacher,

[LIST=1]
[*]Creating accounts and letting students set password on first login.
I think pre set passwords in this kind of environment will be a hassle.
[*]Automatically have a read only public folder mounted in each new users home folder linked to a folder on the teachers desktop/home.
[/LIST]

In case you have a small budget you can also check out Userful Multi seat. 
Basically the same as Edubuntu but the installation and management is even more smooth.
There is a license fee for Userful but I'm not sure how they license or how much.

[http://www.youtube.com/watch?v=XdB5G7cP5mM](http://www.youtube.com/watch?v=XdB5G7cP5mM)
[http://www.userful.com](http://www.userful.com)

No problem! Good luck!

---

### Post by snowguy on 2012-08-07
Hi Sketchies, I am facing a similar problem and am interested in hearing how it went for you? What did you end up deciding on?

---

### Post by SeijiSensei on 2012-08-08
> **kgatan said:**
> Automatically have a read only public folder mounted in each new users home folder linked to a folder on the teachers desktop/home.


When new accounts are created, the home directories are based on the contents of /etc/skel.  So if you place a symlink to the shared directory in /etc/skel, it will automatically appear in each new account.

```
cd /etc/skel
sudo ln -s /path/to/the/shared/directory

```

You need to control access on the folder itself.  If you want to give the teachers write access to the folder, you should create a group for them and set the permissions on the shared folder to grant write access to the group.

```

sudo groupadd teachers
sudo useradd --gid teachers teacher1
cd /path/to/the/shared
sudo chmod 775 directory

```

That creates a "teachers" group, then creates a new user "teacher1" with primary group "teachers".  The last two lines grant full privileges on the shared directory to the folder's owner and to the teachers group, but only read-only privileges to everyone else.

---

