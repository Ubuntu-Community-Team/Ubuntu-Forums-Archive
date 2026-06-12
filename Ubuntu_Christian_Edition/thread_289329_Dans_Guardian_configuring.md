---
title: "Dans Guardian configuring"
date: 2006-10-30
forum: Ubuntu Christian Edition
---

### Post by NotNutts on 2006-10-30
Hello!  I just installed Ubuntu Edgy (upgrading from Dapper didn't work, but a fresh install worked like butta!) and then loaded Dans Guardian using your script.  It works great!  However, now I can't see the shared folders on the LAN (using SAMBA).  Configuring Dans is a nightmare--can anyone help?

YBIC
Brian

---

### Post by tonhou on 2006-10-31
Hi Brian,

Firehol firewall will be blocking. Could you try adding:

**server samba accept**

to /etc/firehol/firehol.conf

You will need to restart firehol:

/etc/init.d/firehol restart

(or just restart computer)

Let us know how it goes.

--Tony

---

### Post by NotNutts on 2006-10-31
I gave this a try using SUDO GEDIT-->still no worky.  Maybe if I described the problem more.   My machine sees 'windows network', but when I click on that, it does not see the individual machine.  It did prior to running the dansguardian script.

Thanks in advance;
Brian

---

### Post by mysticrider92 on 2006-10-31
Dansguardian probably think the files you are trying to get are bad for your computer. Open up the app to configure Dansguardian (System > Administration > Configure Parental Controls) and go to the blocked file extensionsm, I assume. In that file, you should see a bunch of notes with # in front of them, and then a list of blocked files types. Delete or add a # sign in front of any that you don't want to block, and that might solve the problem.

---

### Post by NotNutts on 2006-10-31
> **mysticrider92 said:**
> Dansguardian probably think the files you are trying to get are bad for your computer. Open up the app to configure Dansguardian (System > Administration > Configure Parental Controls) and go to the blocked file extensionsm, I assume. In that file, you should see a bunch of notes with # in front of them, and then a list of blocked files types. Delete or add a # sign in front of any that you don't want to block, and that might solve the problem.

I've already #'d out all file types in bothe mime and app-->still no worky!

---

### Post by NotNutts on 2006-11-01
I bet it's the firewall included in the distro.  Is there any way to temp-disable the firewall (to troubleshoot)?  How do I configure firehol?

---

### Post by Greevous on 2006-11-02
I believe I have installed Dans Guardian, but I do not know how to configure settings, or if it's even running at all. Is there some way I can make sure it is running?

---

### Post by bmathis on 2006-11-02
> **Greevous said:**
> I believe I have installed Dans Guardian, but I do not know how to configure settings, or if it's even running at all. Is there some way I can make sure it is running?

to see if its running try ```
ps -e | grep dansguardian
```

the conf file is located in /etc/dansguardian/ with a bunch of other files for blocking, etc... PM me with exactly what you need done and I can more than likely walk you through it.

---

### Post by NotNutts on 2006-11-02
> **Greevous said:**
> I believe I have installed Dans Guardian, but I do not know how to configure settings, or if it's even running at all. Is there some way I can make sure it is running?

The easiest way to check is to attempt to go to a porn site--I know it blocks [www.porn.com](www.porn.com) 

The only way I know to configure is by running the script found here: [http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-content-filtering-only.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-content-filtering-only.html)
And then using the GUI provided.  You have to edit some text files and comment/uncomment to configure.  Now if I could only figure out how to configure the firewall...

---

### Post by Greevous on 2006-11-02
Needless to say, that didn't work. I tried the ps = e... and nothing visibly happened, so I simply typed "dansguardian" into the terminal and I got this:

```
Error reading file:
Error reading file:
Error opening exceptionvirussitelist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration files

```

Any more ideas?

---

### Post by A-Dream on 2006-11-03
Hi, i installed this script on a regular ubuntu 6.10 desktop and i must say that it works great, but i have 2 questions: first: how can I adjust the filter level (for example, only disable hardcore and softcore porn but not nude images or something)? It would be great if the configure panel could be used to simply adjust the filter level between none, basic (only real porn), advanced (porn + nude pictures), and extreme (all nude content), or something like that.

Second, it would be great if the parental control center got a specific password other than the account password - my children know that password because it is also required to login to ubuntu and to adjust simple setitngs like the time. Is it somehow possible to create a manual password for the application?

If the above two things could be solved I think this application could become a very nice feature of the ubuntu desktop.

---

### Post by NotNutts on 2006-11-03
> **A-Dream said:**
> Hi, i installed this script on a regular ubuntu 6.10 desktop and i must say that it works great, but i have 2 questions: first: how can I adjust the filter level (for example, only disable hardcore and softcore porn but not nude images or something)? It would be great if the configure panel could be used to simply adjust the filter level between none, basic (only real porn), advanced (porn + nude pictures), and extreme (all nude content), or something like that.

Second, it would be great if the parental control center got a specific password other than the account password - my children know that password because it is also required to login to ubuntu and to adjust simple setitngs like the time. Is it somehow possible to create a manual password for the application?

If the above two things could be solved I think this application could become a very nice feature of the ubuntu desktop.

I solved the password problem by creating a separate login for my kids with a different password than the root password.  As to configuring, its not very user-friendly, thats for sure.  I haven't figured it out either.  Plus, I still haven't figure out how to config the firewall--my original question.

Hope that helps!

---

### Post by tonhou on 2006-11-03
> Hi, i installed this script on a regular ubuntu 6.10 desktop and i must say that it works great, but i have 2 questions: first: how can I adjust the filter level (for example, only disable hardcore and softcore porn but not nude images or something)? It would be great if the configure panel could be used to simply adjust the filter level between none, basic (only real porn), advanced (porn + nude pictures), and extreme (all nude content), or something like that.
 
There is such an adjustment relating to the weighting of objectionable material on a page - this may or may not satisfy what you want. I believe Jereme is including ability to adjust this in next version panel. In the mean time you can go to:

/etc/dansguardian/dansguardianf1.conf

then scroll down to "naughtyness limit". By default it is set for young children = 50, for older children or adults it can be changed to 100 - 160.

Hope this is helpful.

--Tony

---

### Post by mhancoc7 on 2006-11-03
Hi all,
I have been watching this thread closely. I wished I had more answers to some of the issues such as the firehol one. 

I do want to note that the scripts are built for Dapper LTS 6.06. So results will vary when using it on Edgy. I will be adding the "Naughtyness Limit" to the next release of Ubuntu CE. It will also be included in the scripts as well. Keep in mind that Ubuntu CE is built from Dapper so the scripts will be built for Dapper as well. After the next release of Ubuntu CE (next week or so) I will be working on some scripts for Edgy. This will not be officially released throught the Ubuntu CE project site, but I will make them available on the forums for those interested. Ubuntu CE will more than likely move to Edgy eventually. I am staying with Dapper for now because of its stability.

God Bless, Jereme

---

### Post by tonhou on 2006-11-04
Yes, the handling of Samba is somewhat of a challenge! I am wondering if along with:
**server samba accept**

that you also try 
**server microsoft_ds accept**

-that is adding it to:
/etc/firehol/firehol.conf

and then restart firehol, or the computer.

--Tony

---

