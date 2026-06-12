---
title: "Home Server"
date: 2016-02-15
forum: Server Platforms
---

### Post by Diego_Vega on 2016-02-15
[FONT=tahoma]Hi i am interested in creating a home file server on my old acer aspire 7741z but i don't know if i should:
>use ubuntu or ubuntu server edition
>Use ubuntu server vs fedora server vs ?????
>use 14.04.3 lts or 15.04(soon to be 16.04:D)>use what packages
Please help[/FONT]

---

### Post by newbie-user on 2016-02-15
Any version of Ubuntu can be turned into a server. You just need to install the necessary packages. If you choose to go with Ubuntu Server, you'll get a command prompt to work with by default, no GUI. If you go with desktop Ubuntu, you'll get a GUI and command line. So it really depends on your preferences. With either installation, you'd have to install some file server such as nfs or samba.

For a server that you want to keep around for a while, you'll probably want to stick to the LTS versions. 14.04 is supported until 2019, so that's a good place to start.

---

### Post by nerdtron on 2016-02-16
For a purely home home file server, then server edition or the desktop edition will do. Even Xubuntu can serve as a file server. Added benefit is included GUI.

Anyway, I should not be saying this but, if your other devices on your network are windows machine, then might as well stick with a windows server and share some folders. Quick and easy.

Of course you can still do it on linux and have fun. Plus you'll learn something new.

---

### Post by MAFoElffen on 2016-02-16
> **nerdtron said:**
> For a purely home home file server, then server edition or the desktop edition will do. Even Xubuntu can serve as a file server. Added benefit is included GUI.

Anyway, I should not be saying this but, if your other devices on your network are windows machine, then might as well stick with a windows server and share some folders. Quick and easy.

Of course you can still do it on linux and have fun. Plus you'll learn something new.
Of course a M$ License for Win Server 2012R2 Standard is $600-$700, Win Server 2012R2 Datacenter is over $1400. And some businesses I consult "tell me" that Samba does a better job managing file shares than Win Server does. (That makes me feel proud, but...) I get paid either way, but that is the what of that.

Two more options are using Webmin with Ubuntu Server, so you have a web browser interface to manage your shares... 

Or Zentyal Server, which is a branch off of Ubuntu and is based on Ubuntu Server Edition. It's GUI uses the zenbuntu-desktop. It also has a web interface. I think it has some really good scripting underneath the hood to automate some of the management tasks of a small business all-in-one server. It's market niche is as an MS Exchange compatible mail server, but it has other roles and uses. I think it would make a good user friendly home server. (Their development version is free.)

But my disclaimer-- they release on Ubuntu LTS versions and are about a year behind Ubuntu on their release. Their support of their pieces and bug resolution of those is not as on the ball as mainline Ubuntu.

---

### Post by mastablasta on 2016-02-16
I will give a few more options on server GUI (server administration via Web browser)

Zentyal - full small business server package, Ubuntu based with canonical backing. two things - community version runs on latest Ubuntu, they reduced the number of apps a lot (not cool if you ask me). their aim is replacement for Microsoft SBS. it's still very easy to use. but their focus is more on small businesses.
Openmediavault - Debian stable based, very intuitive and easy to setup. plenty official plugins and apps, many 3rd party ones.
Nethserver - CentOS/RedHat based, very easy to use
ClearOS - CentOS/RedHat based, easy to install and all, but some plugins need to be payed for (or you can make them yourself). similar to Zentyal focused more on business

--
Ajenti - very light and usefully web interface for server administration that can be easily installed on Debian, Ubutnu or Centos.

if you want to share your files with outside world do not forget about installing fail2ban or similar program and explore the option of owncloud or seafile.
if you are just transferring files use sFTP, for sharing locally you can use Samba.

---

### Post by nerdtron on 2016-02-16
> **MAFoElffen said:**
> Of course a M$ License for Win Server 2012R2 Standard is $600-$700, Win Server 2012R2 Datacenter is over $1400. And some businesses I consult "tell me" that Samba does a better job managing file shares than Win Server does. (That makes me feel proud, but...) I get paid either way, but that is the what of that.

Two more options are using Webmin with Ubuntu Server, so you have a web browser interface to manage your shares... 

Or Zentyal Server, which is a branch off of Ubuntu and is based on Ubuntu Server Edition. It's GUI uses the zenbuntu-desktop. It also has a web interface. I think it has some really good scripting underneath the hood to automate some of the management tasks of a small business all-in-one server. It's market niche is as an MS Exchange compatible mail server, but it has other roles and uses. I think it would make a good user friendly home server. (Their development version is free.)

But my disclaimer-- they release on Ubuntu LTS versions and are about a year behind Ubuntu on their release. Their support of their pieces and bug resolution of those is not as on the ball as mainline Ubuntu.

^Yup. My bad. I just assumed that since he's just using a laptop at home [FONT=tahoma]"old acer aspire 7741z[/FONT] ", it comes with windows.

Anyhow Samba is still a good solution and definitely worth the effort.

---

### Post by Diego_Vega on 2016-02-16
> **newbie-user said:**
> Any version of Ubuntu can be turned into a server. You just need to install the necessary packages. If you choose to go with Ubuntu Server, you'll get a command prompt to work with by default, no GUI. If you go with desktop Ubuntu, you'll get a GUI and command line. So it really depends on your preferences. With either installation, you'd have to install some file server such as nfs or samba.

For a server that you want to keep around for a while, you'll probably want to stick to the LTS versions. 14.04 is supported until 2019, so that's a good place to start.
But how can i even do that?

---

### Post by QIII on 2016-02-16
Hello!

If I understand correctly what you want to do, [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba) might be helpful.

This is not really an "answer" as such, but reading through a few things there might help you jot down a bunch of questions that are more direct and detailed.  Don't worry if none of it makes any sense to you. If it creates more questions than answers, then you can always ask and we will be happy to answer!

Cheers!

---

### Post by MAFoElffen on 2016-02-16
A basic answer is that Windows shares files through a protocol called smb services. smb is a common protocol to share things between various platforms. Samba provides Linux with those services. 

Basic Samba services can be done with an Ubuntu Desktop , just by going to nuatilus > directory properties > share ... and it asks to install the appropriate Samba pieces to provide that. That would be equivalent to a Windows machine doing a Workgroup share (with a few differences). Which goes back to someone's comment, that if it already had a version of Windows, it can already do a basic smb "share" of files through workgroup...

Samba Server is a more robust and fully featured service provider. You can configure your security on the who and where from, in detail, if needed... It provides you with , user, group and ACL rule based security options, as well as configuring other things... t bab1 could explain that in more detail, if needed.

To summarize, you want central access to your files, with enough security to keep those files safe. To do that, it needs access to. i.e.: network access, permissions, security and speaking the same language.

If it is was fully featured media center type of server that you were looking into, instead of just file sharing... then MythBuntu(?)

---

### Post by newbie-user on 2016-02-17
> **Diego_Vega said:**
> But how can i even do that?

On either Ubuntu Desktop or Ubuntu Server, you have the command line available. So open up a terminal and type: sudo apt-get install samba

---

### Post by ian-weisser on 2016-02-17
When I was learning how to create a server, I found Virtual Machines to be handy, easy testbeds without cluttering up your desktop/laptop.

VirtualBox (and several other quite good hosts) are in the Software Center.
Install any flavor of Ubuntu that you want to try into the VM, then install Samba for file sharing, then install whatever you want for other services.
Then try to use it.

I have a lovely 14-year-old Toshiba laptop that cannot run pretty GUIs anymore, but runs Ubuntu Server (no GUI) perfectly well.

Location planning:
Near a good outlet. Avoid fire hazards.
Near your router is preferable. Connect using ethernet, not wireless, when possible.
Good airflow, dust-free, confortable temperature and humidity. Not an attic or basement or closed closet.
Fans make noise, especially in the middle of the night. Don't make sleepers listen to them.
Laptops have blinky lights that can flash a long way at night, or distract visitors.

My own is happily humming on the very top of a hallway bookshelf, lid closed, next to the router. Outlet behind the bookshelf. No exposed cords, clean and safe.

Suggestions:
Use a 15.10 flavor, and upgrade to 16.04 when released. If you set up services for 14.04 (Upstart), you will need to learn them all over again for systemd.
Use automatic security upgrades.
Use SSH to communicate with the server remotely. Set up keys properly every time. Always use keys!
Learn to use the shell. It's faster, easier, and more flexible.

Keep a journal of your changes and customizations. You think you will remember...but you won't. Take notes, list references.

Oh, and have a good time.

---

