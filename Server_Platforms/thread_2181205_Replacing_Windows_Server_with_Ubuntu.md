---
title: "Replacing Windows Server with Ubuntu"
date: 2013-10-16
forum: Server Platforms
---

### Post by Jonny87 on 2013-10-16
Im wondering if its possible to completely replace win serv with Ubuntu. Can Ubuntu be set up for windowa update server, active directory (or equivalent). and as a Windows activation server

---

### Post by lingpanda on 2013-10-16
Not sure what you mean by Windows Update and Activation server. As a ADDC yes. See Samba4

---

### Post by Jonny87 on 2013-10-16
Sorry that message was abit rushed as i was reaching the end of my break.
Windows Server is has the ability to act as an update server, where a company can direct there individual desktops to update from instead of all downloading from the internet. Same with Activation. I just wondered if it ws possible for Ubuntu server to take on these roles so there would be no need for a windows server.

---

### Post by SeijiSensei on 2013-10-17
There is no equivalent to activation because Ubuntu is free and open.  There's nothing to activate.

As for using it as a centralized update server, it depends.  It's possible to have an Ubuntu server be a central repository for packages that can be installed on other machines running Ubuntu.  I don't know of any method for it to archive Windows updates for later redistribution since there isn't any mechanism within Ubuntu to communicate with the Microsoft servers.  These types of services are entirely proprietary to Microsoft and are not going to be replicated on machines running Linux (or any non-Windows OS for that matter).

---

### Post by Jonny87 on 2013-10-17
> **SeijiSensei said:**
> There is no equivalent to activation because Ubuntu is free and open.  There's nothing to activate.
Yes I'm aware that Ubuntu doesn't need to activation, I was meaning for windows activation.

> **SeijiSensei said:**
> As for using it as a centralized update server, it depends.  It's possible to have an Ubuntu server be a central repository for packages that can be installed on other machines running Ubuntu.  I don't know of any method for it to archive Windows updates for later redistribution since there isn't any mechanism within Ubuntu to communicate with the Microsoft servers.  These types of services are entirely proprietary to Microsoft and are not going to be replicated on machines running Linux (or any non-Windows OS for that matter).
Yea I thought it might be a long shot, I know what Microsoft are like. I just thought that perhaps some one may have come up with a way to make it work.

---

### Post by lingpanda on 2013-10-17
> **Jonny87 said:**
> Sorry that message was abit rushed as i was reaching the end of my break.
Windows Server is has the ability to act as an update server, where a company can direct there individual desktops to update from instead of all downloading from the internet. Same with Activation. I just wondered if it ws possible for Ubuntu server to take on these roles so there would be no need for a windows server.
OK for WSUS you can try [http://www.nitrobit.com/updateserver.html](http://www.nitrobit.com/updateserver.html) however I've never used it. Let me know if you give it a whirl.

---

### Post by codybricesands on 2013-10-17
Whelp, I used to run a windows home server until i found ubuntu. But in your case it can depend on what you use on your windows server. However you might want to look at what you got on your windows server and research server software like that for ubuntu.

---

### Post by SeijiSensei on 2013-10-18
He's talking about professional ("enterprise-class") Windows servers, not one you would use in your home.  The Windows ecosystem is built on a variety of highly-integrated, and highly proprietary, applications like Active Directory, Exchange, etc.

---

### Post by Jonny87 on 2013-10-18
> **lingpanda said:**
> OK for WSUS you can try [http://www.nitrobit.com/updateserver.html](http://www.nitrobit.com/updateserver.html) however I've never used it. Let me know if you give it a whirl.

Thanks for that, I'll give that ago and let you know if it does what I need.

---

