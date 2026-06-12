---
title: "Axigen Email Server - Clamav Setup Help"
date: 2007-08-02
forum: Server Platforms
---

### Post by Jixxon on 2007-08-02
I am running an Axigen email server on my Ubuntu box and it works great. I was able to set up spamassassin without any trouble. My question is about adding antivirus by installing clamav.

I was wondering if anyone else has done this (using 7.04) and could offer a how-to or some guidance on the process.

I found the following how-to link from Axigen on using apt-get to install clamav on a debian system (assumed it would work for Ubuntu): [http://www.axigen.com/forum/showpost.php?p=187&postcount=4]("http://www.axigen.com/forum/showpost.php?p=187&postcount=4")

I completed the first step (installing via apt-get) and then stopped. The four items listed in the install command actually turned out to be eight. (There were some other items that were downloaded (dependencies?) that were needed for clamav).

After the install the terminal stated that four of the items were installed but were not configured because they depended on other installed items being configured. The other items that needed configuration were in the same list. I hope I explained that right... it appears the four items needed each other to be configured so they each would work on their own.

Maybe I should have continued with the directions and this was what was supposed to happen. The how-to in the link I gave didn't give much detail on the process. I stopped so I didn't mess anything up permanently. Has anyone else done this with an Axigen email server.

Thanks for the help.

---

### Post by JohnnyPiratefish on 2007-08-02
I'd avoid using ClamAV right now - it's definitely the best solution for doing anti-virus work, but there's some issues with the current version that Ubuntu has posted - version .90.2.

I've already posted this ClamAV issue on the forums, without any response - [here]("http://ubuntuforums.org/showthread.php?t=513571").

I've written an anti-spam server setup called the Piratefish which uses Postfix, MailScanner, SpamAssassin and ClamAV together to build a complete secure anti-spam email relay - see [Piratefish.org]("http://www.piratefish.org") for more information there.

Right now, my users are experiencing troubles where emails get stuck in the processing queue, and literally clog in the server while the ClamAV daemon times out trying to scan the messages.  There's also some kind of denial of service thingy being mentioned as well - so for now I'd recommend avoiding ClamAV (you can still install it) until a freshclam reports that you're using something newer than .90.2.

The current version, according to freshclam, is .91.1 - and compiling from source is a total pain in the butt, and will make upgrading in the future even more painful.

---

### Post by Jixxon on 2007-08-02
Great information to know (about the clamav problems) - Thank you! I also received a response from Axigen on the issue and there is an updated install how-to that I couldn't find before. This should solve my apt-get install problem.

As you suggested I will probably get the antivirus installed and hold on implementing it until the issues with the current clamav version are worked out. I will do some more research on it.

Thanks for the Piratefish.org link as well. I will definitely check it out!

---

