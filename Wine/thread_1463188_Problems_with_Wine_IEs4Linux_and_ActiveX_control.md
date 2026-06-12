---
title: "Problems with Wine IEs4Linux and ActiveX control"
date: 2010-04-26
forum: Wine
---

### Post by wijit on 2010-04-26
First of all I'd like to brieftly describe the system I use. Hardware is a ECS Green 733 notebook with 256MB RAM. OS is Jaunty release of Ubuntu. Recently management assigned a new task to me - security on a campus. Regularly, I have to scan 31 cctv's via the internet. The server needs a client web browser to install webrec.cab which contains ActiveX controls. I feel reluctance to go back to Windows so I try hard to find ways to do the job without Windows. I found IEs4Linux allow ones to run IE6 (and few olders) on Linux through Wine. I followed steps suggested in [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu) with minor modification - "jaunty" in places of "edgy". Problems arose just after the extraction of ies4linux tar file and before the the first dialog to start. There was a warning in red color saying that the software was designed to work with the latest version of Wine (0.9.x) and I seemed to use older version. In fact, I was using version 1.1.42 of Wine. Next problem, during the installation, was a pop-up dialog saying a program called rundll32.exe faced serious error and needed to close. However, the installation did not stop. It went on and finished with no report about any problems. IE can be invoked by double clicking on an icon on the desktop or typing "/bin/ie6" in terminal. The first run it links to the congratulation page of tatanka website. Another problem happenned after closing the IE window. The program's process(es) did not close. It might be caused by my small RAM. However, when the program was turned on and off two or three times their processes became zombies when looked in System Monitor. The whole system was then slow down like a slug. The last problem occured when I connected to the cctv server. The server asked for installing a program called "webrec.cab", a program of an ActiveX kind, but the installation had never taken place. There are suggessions at [http://www.gagme.com/greg/linux/activex-linux.php](http://www.gagme.com/greg/linux/activex-linux.php), but none works for me. To my experiences, Wine works fine for small utilities such as file format converters (single exe).

---

### Post by wijit on 2010-05-19
Hi,
I'm back here again. According to conversation at [http://www.codeweavers.com/support/tickets/browse/?ticket_id=774761;s_subject=ins;tscurPos=100](http://www.codeweavers.com/support/tickets/browse/?ticket_id=774761;s_subject=ins;tscurPos=100), installation of webrec.cab may not be posible with current version of Wine. So this issue may be closed with no solution. However, zomby problem should be seen as a bug still. As I upgraded the OS to Lucid now and I don't want to install Wine and IE again, I'm sorry for unable to provide system info any more. However, simulation of the problem is very easy, just install Wine and IE and then open and close IE again and again. When you feel your system slow down you open System Monitor and you should see several processes of IE. If you refresh the result of System Monitor about an hour or two after that those processes will have zomby status.

---

### Post by asdfoo on 2010-05-20
ok, first of all, please use line breaks to space out your message, putting it all on one line is extremely hard to read.

You mention Wine 1.1.42, this version had problems with installers.  I suggest you try 1.1.44.

---

### Post by wijit on 2010-05-31
Please forgive me for the untidy story, adsfoo.

Thanks for the advice. However, after reading at [www.winehq.org](www.winehq.org), I saw only v.1.0.1 was reported stable. So I try installing it. Then I try installing IE4Linux again and it seems to me that IE4Linux was happy with this version of Wine. IE works fine and no zomby(ies) remain in the memory. I think this part of my problems was solved by installing Wine v. 1.0.1 (I did from Synaptic) and IE4Linux which in my case I select IE6.

The other part of my problem is about installing ActiveX that coming in with a call to the server [http://cctv1.rmutk.ac.th](http://cctv1.rmutk.ac.th) for the first time. The software cannot be installed and this still be a problem of mine.

However, I think the unsolved problem is not really related to Wine so I decide to ask someone at IE4Linux for a help.

Thank you everyone who read.

---

