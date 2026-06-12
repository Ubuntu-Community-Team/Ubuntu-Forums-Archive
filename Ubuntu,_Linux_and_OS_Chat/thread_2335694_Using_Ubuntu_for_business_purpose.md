---
title: "Using Ubuntu for business purpose"
date: 2016-08-31
forum: Ubuntu, Linux and OS Chat
---

### Post by jagal2 on 2016-08-31
Hi,

We were using windows for long time in our official computers. Now we are thinking about use Ubuntu in all future computers (Laptops/Desktops) . It will be very help full if some one answer the following questions.

1. Is there any special edition Ubuntu for business users? (like Pro/Ent editions of Windows)
2. Is it legal using pre-installed Ubuntu for business purpose? (Dell Laptops we received recently)
3. Is there any license fee or yearly payments for using Ubuntu for business purpose?
4. Where can we get support for any critical issues? 
5. Do we need any service/support contract? if answer is yes. To whom we have to approach in Saudi Arabia?
6. Is this system/application updates free for ever?
7. Where can we find the device drivers? (We could not find Ubuntu drivers in Dell support.)

Thanks in advance for these silly questions of a windows user.. 
 
Jagal

---

### Post by slickymaster on 2016-08-31
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by oldfred on 2016-08-31
Ubuntu is free. There is one Ubuntu but many flavors.
       [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors) 
    
Ubuntu has every two years, 14.04, 16.04 etc LTS or long term support versions. Use can use those for 5 years from first release. But most update every 2 years. The versions released in between only have 9 months of support.  So in October when 16.10 comes out it will only be supported for 9 months.

[http://www.ubuntu.com/legal](http://www.ubuntu.com/legal)
Above page offer link to Ubuntu Advantage or Canonical's support packages for business.
[http://www.ubuntu.com/legal/ubuntu-advantage](http://www.ubuntu.com/legal/ubuntu-advantage)

I would think if you bought thru Dell's business systems, they may also offer support.

If you bought Dells with Ubuntu pre-installed you have the drivers.
Dell does often have a set of drivers/updates called sputnik for any hardware they use that is not supported in the current Ubuntu. With 12.04 they had a sputnik, but by 14.04 all those drivers/updates were included in standard Ubuntu. Sometimes settings may still be required.

 New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/) 

I have a Dell SFF and it just worked with then current Ubuntu.

 Dell Inspiron 3647 SFF Haswell i3 
[http://ubuntuforums.org/showthread.php?t=2275234](http://ubuntuforums.org/showthread.php?t=2275234)

---

### Post by sudodus on 2016-08-31
Welcome to the Ubuntu Forums :-)

- I wish you good luck using Ubuntu for business purpose.

- You should realize that we are volunteers at the Ubuntu Forums. I think we can give you good answers as peers, but we do not represent Canonical, the company, that is responsible for Ubuntu.

> **jagal2 said:**
> Hi,

We were using windows for long time in our official computers. Now we are thinking about use Ubuntu in all future computers (Laptops/Desktops) . It will be very help full if some one answer the following questions.

1. Is there any special edition Ubuntu for business users? (like Pro/Ent editions of Windows)

Maybe. The desktop and server versions are the same for all users, but there are other versions too, see this link [http://www.ubuntu.com/](http://www.ubuntu.com/) and links from it.
> 
2. Is it legal using pre-installed Ubuntu for business purpose? (Dell Laptops we received recently)

Yes.
> 
3. Is there any license fee or yearly payments for using Ubuntu for business purpose?

Not for using the desktop version and server versions available for download via the internet [http://www.ubuntu.com/download](http://www.ubuntu.com/download)
> 
4. Where can we get support for any critical issues? 

I think you find it via this link: [https://buy.ubuntu.com/](https://buy.ubuntu.com/)
> 
5. Do we need any service/support contract? if answer is yes. To whom we have to approach in Saudi Arabia?

Ask Canonical, for example via [mailto:sales@canonical.com](mailto:sales@canonical.com)
> 
6. Is this system/application updates free for ever?

There is no known date, but companies and technologies do not live forever ;-)
> 
7. Where can we find the device drivers? (We could not find Ubuntu drivers in Dell support.)

Most device drivers come with linux and are used automatically. There are proprietary drivers for some hardware, that you get either via Ubuntu or directly from the hardware manufacturer. I should tell you, that some hardware manufacturers provide no drivers for linux, so this might be a weak spot, particularly for peripheral devices.

Dell computers are known to run well with Ubuntu. You might need proprietary drivers for graphics and wifi. Some very new and powerful graphics cards (e.g. for gaming) are not supported yet.
> 
Thanks in advance for these silly questions of a windows user.. 
 
Jagal

---

### Post by buzzingrobot on 2016-08-31
On drivers:  Drivers are included in a Linux install image. So, when you install a system, you also install drivers. The Linux kernel identifies the various hardware components when the system boots and loads the appropriate drivers. As sudodus mentioned, some exceptions exist. (FYI:  Intel provides good Linux support for the graphics capabilities built into its CPUs. If you're using typical office and business software, then Intel video support should be just fine. You won't have to worry about drivers for it.,  It's there by default.)

You mentioned not finding Ubuntu drivers on the Dell sites. If those Dells have Ubuntu preinstalled and you are having driver problems, I'd take that up with the vendor that supplied the hardware.

If the Dells do not have Ubuntu preinstalled, I recommend doing a full install on one machine for testing and evaluation before doing installs on all the machines. It's also a good idea to keep that machine around after you've migrated to Ubuntu to test and verify updates, new software, etc., before applying business-wide.  This applies to any operating system, not just Linux.

---

### Post by SeijiSensei on 2016-08-31
> **jagal2 said:**
> 6. Is this system/application updates free for ever?
Yes, most of the software in an Ubuntu distribution is licensed under the [General Public License]("https://www.gnu.org/licenses/licenses.en.html") which permits unlimited transfers of the software as long as source code is provided as well.  (The source code is available on Ubuntu's servers, but isn't typically included on the installation discs for space reasons.)  Some software has [even more liberal]("https://opensource.org/licenses") licensing policies.

However each specific release of Ubuntu has an "end-of-life" date which you can see here: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases).  A "long-term support (LTS)" version comes out every other April and includes a guarantee of five years of support.  The releases are numbered by year and month, so the current 16.04 release came out in April of 2016, and since it is an LTS release, it has support through April of 2021.  The 14.04 release which I use has support through 2019.

> 7. Where can we find the device drivers? (We could not find Ubuntu drivers in Dell support.)
There are a few pieces of proprietary hardware for which drivers may be difficult to find, but most all other drivers for video adapters, network cards, etc., come with the standard Linux kernel.  If Dell is selling hardware that is Linux-compatible, I'd guess all the drivers come with the kernel.  That's especially true for all-Intel hardware which Dell sells a lot of.

More generally....

Your biggest task is identifying every single function in your office that is currently supported on Windows and determining whether it has a Linux equivalent.  If you have artists that need Adobe Photoshop, for instance, Linux isn't a good choice unless you can get those folks to adapt to the GIMP, often not an easy task.  If you're using specialized proprietary software that isn't browser-based, Linux may be a non-starter for those functions as well.  For ordinary office tasks, LibreOffice is fine, though it looks more like versions of Microsoft Office before the invention of the "ribbon."  One program I use that has no good open-source equivalent is Microsoft Access; LibreOffice Base doesn't come close.  

Other possible issues include whether you use Microsoft Exchange, MS "domains" for network management, or other highly proprietary pieces of software.  You can migrate to open alternatives for all of these, but it will take time and effort.

You should also try a couple of different desktop environments before deciding on one to standardize upon.  Along with the standard Unity desktop, take a look at [Kubuntu]("http://www.kubuntu.org/"), [Lubuntu]("http://lubuntu.net/"), and [Xubuntu]("http://www.xubuntu.org/").  You might set aside one current Windows machine with 4 GB or more and install [VirtualBox]("http://www.virtualbox.org/").  Then you can install all the various Ubuntu flavors side by side into separate virtual machines for comparison shopping.

---

### Post by jagal2 on 2016-09-01
Hi Everybody,

Thank you very much for support.

Now I am more confident to take a decision like moving to Ubuntu.  I hope, I can solve any issue may face in future, with the help of fast response from the people like you.. 

Thanks again,
Jagal

---

### Post by kurt18947 on 2016-09-01
There is another resource available - askubuntu.com. I get the impression that askubuntu.com has a closer connection to Canonical than this forum. I'd probably still want some sort of non-volunteer support if I were supporting many business users.

---

### Post by pfeiffep on 2016-09-01
> **jagal2 said:**
> Hi Everybody,

Thank you very much for support.

Now I am more confident to take a decision like moving to Ubuntu.  I hope, I can solve any issue may face in future, with the help of fast response from the people like you.. 

Thanks again,
JagalConsider one of the lighter weight versions such as Ubuntu MATE; this will provide a consistent platform with reasonable response for a diverse age of hardware.

---

### Post by user1397 on 2016-09-02
> **jagal2 said:**
> 1. Is there any special edition Ubuntu for business users? (like Pro/Ent editions of Windows)No, but there are paid support options offered by Canonical.
> 2. Is it legal using pre-installed Ubuntu for business purpose? (Dell Laptops we received recently)Yes.
> 3. Is there any license fee or yearly payments for using Ubuntu for business purpose?No, but if you want paid support you have to purchase a paid support plan from Canonical.  The OS itself and all updates are free always.
> 4. Where can we get support for any critical issues? [http://www.ubuntu.com/management](http://www.ubuntu.com/management)
> 5. Do we need any service/support contract? if answer is yes. To whom we have to approach in Saudi Arabia?No, you don't need a contract to use Ubuntu, but if you want paid support then there is an option, see above.  Not sure about Saudi Arabia, I would just contact Canonical and ask them.
> 6. Is this system/application updates free for ever?Yes, but each Ubuntu version has an end of life.  For enterprise you would stick with the long term support (LTS) versions which feature 5 years of support.
> 7. Where can we find the device drivers? (We could not find Ubuntu drivers in Dell support.)Drivers are usually automatically installed, but there is a drivers management app included by default on Ubuntu.  If your hardware requires a driver that isn't included in Ubuntu's repositories, then you may have to hunt them down online, but there are a few exceptions where drivers either don't work very well or there aren't any for a particular hardware.

I would recommend sticking with regular Ubuntu for maximum assurance of stability/compatibility with everything.  I would suggest installing Ubuntu and testing out all hardware components on one of your computers before going with a full deployment across the enterprise.  Ubuntu is great for servers as well not just workstations.

If you have any other questions, don't hesitate to ask :)

---

### Post by Tadaen_Sylvermane on 2016-09-03
Bears repeating. Stick with LTS releases for business / production usage. You don't want to be stuck in an upgrade cycle every 9 months if possible. Stay with the longest support periods possible.

---

### Post by kurt18947 on 2016-09-05
Something else to research and I don't know the answers. If you were to choose one of the 'flavors' of Ubuntu such as Xubuntu, Lubuntu, Ubuntu-Gnome etc. I'm not certain about 5 years support on non Canonical bits such as XFCE, LXDE etc.  I think there may be 3 years support on those.

---

### Post by TheFu on 2016-09-05
Your questions have been answered well above.  But there are important questions NOT asked.

I've been asked to move some clients to Linux a few times.  For their needs, it didn't make sense due to the costs to move proprietary, custom, Windows-only, software and drivers to Linux.  It would have required about 20 yrs for any savings to be seen and companies can't wait that long for a ROI.

Don't make this decision without real data from all the users and upper management.  If the CEO isn't behind this, forget it. It has to come from the top down and the CEO has to be clear that Linux/Ubuntu is the way forward, PERIOD.

In many offices, things like doing normal documents, spreadsheets, web stuff, creating PDFs ... that stuff is easy for Linux.  The harder things come when interfacing outside the office with other companies.  If they don't use the same tools, there are slight conversion issues.  Pagination will be different.  Fonts that aren't exactly the same will be substituted and cause issues.  Forget about using the built-in editing, comments and versions.  Those aren't compatible between the MSFT and non-MSFT tools, IME.

Spreadsheets .... aren't 100% compatible for extreme power users.  Any VB addons probably won't work.

The guys in Sales will probably be addicted to MS-Outlook. Many will have purchases addons to make their contact management more efficient (so they believe).

So ... begin by making a list for each user of all the tools they need and prioritizing the importance for each. If most of the tools have Linux alternatives, then there is a good chance things will work out.  You will probably need 1 or 2 Windows machines with remote desktops so people can remote in from their Linux desktops and do things with native Windows tools.  Accessing Windows needs to be slightly inconvenient so people do it less and less over time. There shouldn't be enough Windows remote desktops available for everyone either.  I've seen this work in other small companies.

Plus accounting will probably stay with whatever system they are using. That fight isn't worth the effort without someone inside accounting leading the changes.

Plus don't forget to let the end-users know all the ways that Linux desktops help IT do their jobs better.  Someone will need to be a Linux guru in-house. That person will need find beginning level training for everyone else.  It also helps if people start switching to the programs they will have on Linux while still running on Windows.  Stop using I.E.  Get them using whatever web browser will be used on Linux.  Same for the email program - stop using Outlook - switch everyone over the Thunderbird. Setup the calendar integrations. It is amazing how great that is.  Start running LibreOffice on Windows. That is likely the tool to replace MS-Office stuff.

BTW, many of your questions assumed things on the Linux world worked in a way like they do in the MSFT world. They don't.  It is common to pay for Linux server software inside a business for highly critical systems. It is very odd for a business to buy desktop software for anyone.  The Redhat CEO runs a community OS - Fedora.  There isn't any paid support available for it.  Basically, the Linux world is VERY different and has a VERY different culture than that for Apple or Microsoft.

A few links that will get you started:
* [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
* [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Plus know that Linux systems **must** have good backups. The best practice for this is daily, automatic, versioned backups. Versioned backups are useful for thousands of issues. They are my #1 security tool as well.

Lastly - when folks here talk about 5 yrs of support with an LTS, that only applies to the core OS, not every program installed.  Some only have 18 months of true support by the community. There is a tool, **ubuntu-support-status**, that can be run to check the support status for all programs installed.  For example, on a 16.04 system (which is LTS), here's the output:
```
$ ubuntu-support-status
Support status summary of 'box':

You have 1589 packages (72.1%) supported until April 2021 (5y)
You have 337 packages (15.3%) supported until April 2019 (3y)
You have 74 packages (3.4%) supported until January 2017 (9m)
You have 9 packages (0.4%) supported until September 2021 (5y)

You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 194 packages (8.8%) that are unsupported

```
I do have a few addon PPAs, so none of those programs will be supported by Canonical. That is to be expected. However, the 74 packages with only 9 months of support might be a surprise to most people.

For a business, "support" means both security patches and helpful answers, with the security patches being much more important than anything else, IMHO.

Good luck to you sir. These are interesting times.

---

### Post by irv on 2016-09-06
After reading through this thread I thought I would throw in my two cents worth.

I have been out of the workforce for 10 years now, (retired). A lot has changed in this past 10 years, but one thing that seems to stay the same. There are so many businesses&#8217; that are stuck in that Microsoft mode. They keep paying MS for using their products.

I had a visit from one of my sons and his family this past weekend and we talked about this subject. He works for a medium to small Engineering firm that is stuck in this same rut, and when I asked him why they don&#8217;t try Linux? His answer was because of all the software they use to run on Windows.

I then asked if they use MS Office? And his reply was sometimes, but most of the work is done using Google Docs.  They do this because a group can all be working on the same doc at the same time.

I told him that a good way to become a Linux base business would be to start with their servers. Then to start using open source software and slowly move away from proprietary software. He then asked the question, What about the specialized software that is needed for the business? He was referring to the CAD software and a few other packages. 

My feeling is these kinds of problems are the reason many businesses&#8217; are not moving to Linux. I think the reason for this is the lack of Linux specialists not talking to people about getting their business&#8217; over to Linux. What an opportunity for Linux programmers to get into the counselling business to helping them get over to Linux.

After reading through TheFu&#8217;s post I think he could start his own Counselling firm. The Industry needs Linux experts.  

Sometimes I wish I was a little younger and still in the workforce. 

This is for you young ones out here. Come on, get on the bandwagon. And another good field to get into is Network Engineering.

---

