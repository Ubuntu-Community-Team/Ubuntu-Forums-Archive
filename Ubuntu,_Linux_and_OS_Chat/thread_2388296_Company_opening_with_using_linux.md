---
title: "Company opening with using linux?"
date: 2018-03-31
forum: Ubuntu, Linux and OS Chat
---

### Post by ra93 on 2018-03-31
Hello!
Last time I made a website which is available here at [https://mmoauctions.com](https://mmoauctions.com)  I wish that I will open company in few months. From start, I want to reduce costs so it is natural that I think about Linux because I do not want to pay for the licenses like Win, Antivirus, MS Office etc. My question is which one distribution will be the best for new users. Mint, Ubuntu or something else? I am thinking about people whose will be working for me. Maybe the first time in Linux. The second question is any viruses on Linux? Do I need have AntiVir? Finally what with software for multimedia like MS Office, PDFs or other. What can be problematic?

---

### Post by jeremy31 on 2018-03-31
Not a support question. *Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by kerry_s on 2018-03-31
take a look at elementary os, it's dead simple.
[https://elementary.io/](https://elementary.io/)
just put 0 where it says custom & download.

you can install libreoffice, there's many choices for pdf readers.

i suggest you lock them down, just make normal accounts for them with no root privileges.

---

### Post by The Cog on 2018-03-31
I think any of the *Bubntu distros is able to support normal office work. The different distros have different appearences, but they are all able to run the same applications - it's just the choice of defaults that differs. The appearances are proabaly going to be your biggest issue, certainly the most obvious. I see lots of posts from people who are happy with mint. My personal preference is for Xubuntu though I don't like their default theme and that's the first thing I change.

LibreOffice is fine for office documentation. The PDF viewer seems to work fine (I can't remember its name). I don't use antivirus regularly, just keep current on software updates. I'm pretty sure you could run a company on Linux. You would save a lot on software licenses, and have a much lower chance of the whole company being wiped out by ransomware etc.

---

### Post by mörgæs on 2018-03-31
Yes, many good reasons for going all-Linux from the beginning.

Have you considered Google Docs in stead of local software like Libreoffice? Makes it easier to distribute and edit documents for multiple users on multiple devices.

---

### Post by SeijiSensei on 2018-03-31
Will you be in an office with networked PCs?  Then I suggest spending a bit of time considering your infrastructure needs.  Probably you want a central server running NFS for file-sharing to the desktops.  Make sure you have it connected to an uninterruptible power supply, and create a well-designed backup scheme including off-site storage of backups.  Maybe a networked printer like [this](http://www.brother-usa.com/printer/modeldetail/1/hl3170cdw/overview) or [this](http://www.brother-usa.com/mfc/modeldetail/4/mfc9330cdw/overview) if you need a scanner.  Will you have a website? E-mail? A domain?

Personally I wouldn't put my business-sensitive documents on any cloud service like Google Docs.

---

### Post by TheFu on 2018-03-31
My company used Linux for all servers and didn't dictate which desktop OS was used to any of our highly-technical staff.  Some used Windows, some used OSX, and some used Linux or BSD.  

There were a few times when Windows was mandatory, since we were consulting with outside clients who only used MS-Office.  To avoid documentation viewing issues, we produced reports natively in MS-Office using a Windows virtual machine. Sometimes you must have MS-Visio, for example.  Final reports were always PDF. 

Sometimes Acrobat Reader for Windows is the only solution - especially with some government-created files. The people creating PDF files often aren't technical, so they force very new PDF versions to be used, which most Linux-based PDF viewers don't support.  PDF creation tools like those from Adobe have a way to say which version of the PDF standard is used.

If your needs are really simple, perhaps using chromebook devices would be a good idea?  Impossible to tell from the limited information provided, but if you only need web browsers on the desktop, but wan't external support that does all the patching, ChromeOS or ChromiumOS are worth considering.
There's also TinyCore Linux which is worth a look if your needs are simple.

And lastly, if you don't outsource accounting, I found that the tools our accountant demanded to use only ran on Windows. It wasn't worth fighting over that.  $500/yr for software to manage corporate finances and keep the accountant happy was well worth it.  Plus there are legal reasons, so it wasn't worth the fight.  I just setup another Windows VM for the accounting software and provided remote access only to the accountant.  

For us, it wasn't about completely removing all MS-Windows/paid software.  It was about limiting the use to where normal users never needed to track licenses and we could manage each license on a single page in a spreadsheet to know know exactly what we had, need, didn't need, and used, while having what was necessary.   We did have a few people really unhappy that we didn't use MSFT servers. The idea that supporting standards-based protocols seemed to freak them out - especially for the people who had been in huge corporate jobs 20+ yrs and just wanted Outlook to work like it always had.   A few excellent folks decided to quit our company over that (and other) reasons.

Many of your questions have been answered in "sticky threads" in these forums already.  There isn't a YES or NO answer to most of  those questions.  IT DEPENDS.  Check out the sticky threads in  the "Security" sub-forum here.  I don't understand what multimedia has to do with PDF or MS-Office. Most companies don't need to support audio or video on their workers desktops.

I would strongly encourage you to get someone engaged who has already done Linux in a business environment so you can work through all the issues BEFORE they happen.  For many businesses, Linux is an excellent fit, but for some businesses, it doesn't make sense. Someone, perhaps not you, should do a detailed analysis of all the tools required for each role in the company.  Make a list.  Work through that list. Verify that inputs from 1 process match outputs to the next and that customers will be happy with the final outputs - whether that is some product or reports or documentation.  Happy customers is critical to a business.

---

### Post by SeijiSensei on 2018-03-31
> **TheFu said:**
> And lastly, if you don't outsource accounting, I found that the tools our accountant demanded to use only ran on Windows. It wasn't worth fighting over that.  $500/yr for software to manage corporate finances and keep the accountant happy was well worth it.  Plus there are legal reasons, so it wasn't worth the fight.
Pretty much any office needs at least one machine running Windows for reasons like this.  Like TheFu, I'd install a copy of Windows into a virtual machine on a Linux desktop (using [VirtualBox]("http://www.virtualbox.org/"), for instance) to handle any software that needs to run on Windows.  I have a few applications that use Microsoft Access, for instance, though my database server runs PostgreSQL with an "ODBC" connector in Windows.)  If that Windows instance needs to access the network server for file storage, you'll probably need to install Samba on it as well as NFS.

---

### Post by QIII on 2018-03-31
I have to echo TheFu and SeijiSensei:  As a businessman I can't ignore the fact that I do business with people who use Windows.  And, frankly, some of the best "business" software is designed for windows, tax and accounting software being foremost among them.

I keep at least two Windows VMs:  One for my own needs and at least one "clean install" (both get regular snapshots).  The latter are used if I need to replicate a client issue in a mixed Windows/Linux environment to find a solution.   I need to be able to develop SQL Server databases and MS Access databases and software that uses them.   It's just a fact of life that to make the income I expect from my business I have to be able to work in both worlds.  I can't afford to wear a hair shirt and be a Linux-only zealot.  I'd miss out on lucrative business opportunities.

---

### Post by mörgæs on 2018-04-01
Ra93, I think you will do yourself a favour if you explained a little more about the company. It seems that people are guessing freely about the nature of your business, the number and kind of employees, the kind of software needed, customers' demands and so on. 

Are you doing graphic design or selling restaurant tickets - or something in between?

---

### Post by ra93 on 2018-04-02
I think about making websites, maybe browser games or web positioning. Since start only a few workers. Can you say a little bit more about antivirus and using it?

---

### Post by mörgæs on 2018-04-02
For these purposes there are lots of stuff available in GNU/Linux and I don't see any need for Windows nor Mac here (Wordpress is for example easier to maintain and manage on GNU/Linux than on a Windows server). However you probably need one computer running Windows for testing how your work behaves in Internet Explorer. 

I can't say anything about antivirus on GNU/Linux because I have never used it and I don't think there is a need. Best you can do is to keep all software updated, be careful who gets to know the root password and keep routers and other network equipment in a good shape. See the security forum for more discussions on the topic.

---

### Post by TheFu on 2018-04-02
> **ra93 said:**
> I think about making websites, maybe browser games or web positioning. Since start only a few workers. Can you say a little bit more about antivirus and using it?

See my earlier post about reading the sticky threads for security questions. [https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338) - those are common questions which have been answered already.

However, any professional insurance may require that you run A/V on all computers inside the business.  My E&O insurance mandates that.

---

### Post by mastablasta on 2018-04-03
> **mörgæs said:**
> For these purposes there are lots of stuff available in GNU/Linux and I don't see any need for Windows nor Mac here (Wordpress is for example easier to maintain and manage on GNU/Linux than on a Windows server). However you probably need one computer running Windows for testing how your work behaves in Internet Explorer. 


or Edge....

if you for example worked with us and wanted an online meeting we would request you use "Skype for Business" (formerly Lync). and while it does have a web version, for some reason it only works well when you use the client. my point, as others wrote, is you would likely need at least one machine with MS products installed. contracts and such (e.g. orders) for example are also exchanged in MS office in our case. 


PDF - i think FoxIT does a good job replacing the Adobe. other viewers work as well, but as some pointed out they might not read the specific versions of .pdf 

Antivirus - on Linux they scan for windows malware. you need to harden you system mostly in other way especially if you plan to do servers and open doors to internet. they hack you with other methods, usually not via virus.

On your windows machine i suggest Windows 10 Enterprise. it's built in defences are very good. If you can't get enterprise version (not sure what you need to be able to buy it) at least get the pro version. don't even think about using Home. you might want to have multiple windows VMs available for tests with various browsers. 

Libre office is quite behind with it's user interface. and i am not talking about the ribbon (i know they plan it). in latest office for example the text and such changes live as you select options. it's for example quite easy to see how the document will look like if you need to make something presentable. there are many such things in latest office versions that make it easy for the user.

---

