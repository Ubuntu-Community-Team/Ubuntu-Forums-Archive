---
title: "Ubuntu Weekly Newsletter #38"
date: 2007-04-29
forum: Weekly Newsletter
---

### Post by Vorian on 2007-04-29
[I]**Disclaimer:**I'm not the author of the UWN, the full credits are listed below.

[/I][SIZE=5][B]UbuntuWeeklyNewsletter/Issue38
[[SIZE=2]https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue38[/SIZE]]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue38")
[/B][/SIZE]

Welcome to the Ubuntu Weekly Newsletter, Issue 38 for the week April 22nd - April 28th, 2007. In this issue we cover Gutsy Gibbon's kick off off development and new additions, the availability of VMware server on Canonicals commercial servers and the Latinamerican Installfest.

[SIZE=5]**UWN Translations**[/SIZE][LIST]
[*] Deutsch - Start one! [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/IssueXX/De](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/IssueXX/De)
[*] Español - [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/IssueXX/Es](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/IssueXX/Es)
[*] Français - Start one! [ https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/IssueXX/Fr]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/IssueXX/Fr")
[*] Italiano - [ http://wiki.ubuntu-it.org/NewsletterItaliana]("http://wiki.ubuntu-it.org/NewsletterItaliana")
[*] Português - Start one! [ https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/IssueXX/Pt]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/IssueXX/Pt")[/LIST][SIZE=5]**In This Issue**[/SIZE][LIST]
[*] Gutsy Gibbon Ready for Development
[*] VMware server available for Ubuntu
[*] Flisol 2007
[*] Meetings and Events
[*] Security Updates
[*] Bug Stats[/LIST][SIZE=5]**General Community News**[/SIZE]

    **Gutsy Gibbon Ready for Development**

  Tollef Fog Heen has announced that the next release, Gutsy Gibbon, is ready for development. The main purpose of Gutsy is improvement and quality. There will not be much in terms of new or experimental features but stabilising and polishing the existing features. Gutsy is being synched with Debian's unstable branch, Sid. Some basic packages have already been updated, including the toolchain (binutils, GCC, glibc). Other important changes:[LIST]
[*] The Java compatible environment in main (gij/gcj) now supports Java 1.5 compatibility.
[*] g77 (Fortran compiler) will be dropped and moved to universe. This will require manual changes in all packages build-depending on g77. To avoid differing naming this will be coordinated with Debian.
[*] A prerelease of GCC-4.2 will be available in the archive and packages in main will be changed so they can be built using this new version.[/LIST]**VMware server available for Ubuntu**

  VMware server has been added to Canonical's commercial software repository as of a few days ago. In order to try it out, add the commercial repostiory through Add/Remove Programs and search for VMware. For the more exact, the package name is vmware-server. You can find further instructions (in French) on Fabian Rodriguez's blog at [ http://www.fabianrodriguez.com/blog/archives/2007/04/27/vmware-server-pour-ubuntu-704-disponible-dans-le-depot-commercial/]("http://www.fabianrodriguez.com/blog/archives/2007/04/27/vmware-server-pour-ubuntu-704-disponible-dans-le-depot-commercial/"). 
  [B]
[SIZE=5]LoCo News[/SIZE][/B]

    **Flisol 2007: Latinamerican Install Fest a success**

  On Saturday 28th of April the "Festival Latinoamericano de Instalación de Software Libre" took place in 18 countries and Ubuntu seemed to be the star in most (if not all) the events. Some pictures available at: [ http://beuno.com.ar/archives/16]("http://beuno.com.ar/archives/16") [ http://www.uluga.com.ar/index.php?q=gallery&g2_itemId=18]("http://www.uluga.com.ar/index.php?q=gallery&g2_itemId=18") [ http://blog.blanco.net.ve/2007/04/feistycita-and-flisol-2007-was-success.html]("http://blog.blanco.net.ve/2007/04/feistycita-and-flisol-2007-was-success.html") 
  [B]
[SIZE=5]Gutsy Development News[/SIZE][/B]

  With the opening of Gutsy as reported above, several major pieces of Gutsy are beginning to fall into place. The toolchain (gcc and friends) has been uploaded and shortly following that, Ben Collins uploaded with first of the new Gutsy kernels. In the GNOME world, 2.19.1, the first of the 2.19 development series leading to 2.20 has been released and the Desktop team has been working hard to get that in. Sebastian Bacher has issued a call for help with the Desktop Team at [ https://lists.ubuntu.com/archives/ubuntu-devel/2007-April/023593.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2007-April/023593.html"). 
 Of course, it was only a matter of time before some breakage happened, this time with a switch on dash on some of the buildds, which Colin Watson announced at [ https://lists.ubuntu.com/archives/ubuntu-devel/2007-April/023594.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2007-April/023594.html"). 
  [B]
[SIZE=3]Helping find the right package for your bug[/SIZE][/B]

  Brian Murray, one of the lead QA people for Ubuntu, has posted a quick howto on the proper package to file against, especially for those bugs whose origin is not clear. You can read more at [ https://wiki.ubuntu.com/Bugs/FindRightPackage]("https://wiki.ubuntu.com/Bugs/FindRightPackage"). 
  [B]
[SIZE=5]In The Press[/SIZE][/B][LIST]
[*] David Sims, at TMCnet, reports that Canonical announced the availability of Sugar Open Source for Ubuntu 6.06 LTS. Sugar Open Source, created by SugarCRM, is a customer relationship management platform, emphasizing a "Web 2.0" architecture and Ajax interface. Sugar Open Source has been translated into 50 languages and has over 300 extensions which enhance and extend the application. "Demand for Ubuntu is growing rapidly among SugarCRM customers who require enterprise-level performance and reliability when running Sugar. Ubuntu offers a great user experience and vibrant community that complements SugarCRM's open source project," said John Roberts, Chairman, CEO and Co-Founder of SugarCRM. Read the full article: [ http://www.tmcnet.com/news/2007/04/23/2539502.htm]("http://www.tmcnet.com/news/2007/04/23/2539502.htm")
[*] Stan Beer, at iTWire, writes that Ubuntu has the easiest install and "Ubuntu advocates are right when they say it's probably just as easy and maybe easier than installing Windows." For Linux to keep growing, Stan thinks white box vendors need to pre-install Linux and believes this will start happening with Dell. Corporate sponsors of the various Linux distributions should also spend as much money convincing hardware vendors the benefits of Linux as development. Read the full article: [ http://www.itwire.com.au/content/view/11532/1023/]("http://www.itwire.com.au/content/view/11532/1023/")
[*] Steven J. Vaughan-Nichols, at Linux-Watch.com, compares the relationship of Sun and Ubuntu with Red Hat and JBoss. Sun and JBoss provide Java application server stacks. Mark Shuttleworth says "We don't want to eat up our way up the development stack; we partner with the best people...[Ubuntu/Sun vs. Red Hat/JBoss] is an interesting contrast. Red Hat feels they need to own the brand, while we partner." Sun wants to make Java an important Linux language and thinks the "software stack [that comes with Ubuntu] is enterprise-ready and high performance." Read the full article: [ http://www.linux-watch.com/news/NS8037937963.html]("http://www.linux-watch.com/news/NS8037937963.html")
[*] Michael E. Callahan, at Tucows, reviews Ubuntu 7.04. He quotes Benjamin Mako Hill, who said, "Free software is produced by expert volunteers who make their time and work freely available - our goal is to ensure that anybody in the world can make the best use of that work, at no charge." Michael is impressed how clean and uncluttered Ubuntu is and how frequently it updates. He thinks Ubuntu is impressive and recommends it for users who want to try Linux. Read the full article: [ http://www.tucows.com/article/1512]("http://www.tucows.com/article/1512")
[*] Steven J. Vaughan-Nichols, at Linux-Watch.com, wonders if Canonical can translate Ubuntu's popular success into business success. While Canonical has established partnerships with Sun for a Java application server stack, SugarCRM with its Sugar Open Source product, and IBM with its DB2 database, it is also expanding its support business. Canonical is close to announcing Ubuntu training and certification (Ubuntu Certified Professional) programs. To continue making progress, Canonical has to build relationships with key ISVs and IHVs like IBM and HP. Steven thinks Canonical has made a "solid first step into the enterprise." Read the full article: [ http://www.linux-watch.com/news/NS7320696260.html]("http://www.linux-watch.com/news/NS7320696260.html")
[*] DesktopLinux.com reports that registration is now open for Ubuntu Live, the first official conference dedicated to Ubuntu. The three-day conference will be held July 22-24, along with the O'Reilly 2007 Open Source Convention, in Portland, Oregon. The conference will include sessions and tutorials run by experts, informing and educating the community, everyone from beginners to power-users. Mark Shuttleworth, Jono Bacon, Jon "maddog" Hall and many other Linux celebrities are scheduled to appear. Read the full article: [ http://www.desktoplinux.com/news/NS7015608958.html]("http://www.desktoplinux.com/news/NS7015608958.html") [ http://www.ubuntulive.com/]("http://www.ubuntulive.com/")
[*] Steven J. Vaughan-Nichols, at Linux-Watch.com, writes about Ubuntu's recently updated trademark license which is published under Creative Commons Sharealike with Attribution license (CC-BY-SA). The trademarks states that Canonical owns Ubuntu, Kubuntu, Edubuntu, and Xubuntu in word and logo form. Any trademarks consisting of Ubuntu or buntu will need permission before use. Non-profits groups advocating the use of Ubuntu are exempt. Remixes, which are derivitives that haven't changed any shared libraries or desktop components are allowed. Read the full article: [ http://www.linux-watch.com/news/NS6581540510.html]("http://www.linux-watch.com/news/NS6581540510.html") and [ http://www.markshuttleworth.com/archives/112]("http://www.markshuttleworth.com/archives/112") (Mark's post)
[*] [OpenBusiness]("https://wiki.ubuntu.com/OpenBusiness") sat down with Mark Shuttleworth for an interview. Mark talks about figuring out how to make a sustainable ecosystem around free software and how to make the econsystem pay for itself. The attraction of Linux cannot be a single killer application, but the system as a whole. Listen to the interview: [ http://www.openbusiness.cc/2007/04/24/interview-with-mark-shuttleworth-how-to-make-a-business-out-of-free-software/]("http://www.openbusiness.cc/2007/04/24/interview-with-mark-shuttleworth-how-to-make-a-business-out-of-free-software/")[/LIST][SIZE=5]**In The Blogosphere**[/SIZE][LIST]
[*] David Wolf, at Seek Alpha, blogs that Ubuntu 6 is better alternative to Windows XP. David thinks Microsoft's initiative to sell a prepackaged suite of applications at $3 won't work when large segments of population live on $1 or less. The initiative is not about stopping piracy, its about stopping the spread of Ubuntu. Read more at: [ http://software.seekingalpha.com/article/33196]("http://software.seekingalpha.com/article/33196")
[*] An anonymous blogger, at Reflection Design, writes about his adventures of setting a dual-boot machine with Windows XP and Ubuntu 7.04. He has no problems with the Gnome Partition Manager resizing his NTFS drive and has no problems installing Ubuntu. He is impressed 3D accelaration works with the restricted drivers easily. Read more at: [ http://reflection-design.dk/?p=127]("http://reflection-design.dk/?p=127")
[*] Dean, at Technical Itch, writes about his impressions of doing an upgrade to Ubuntu 7.04 from 6.10. He finds the upgrade instructions easy to follow and finds all his existing applications working after the upgrade. Troublesome videos worked flawlessly after the installation of codecs. Dean thinks Ubuntu 7.04 is a top notch product. Read more at: [ http://technical-itch.co.uk/2007/04/20/ubuntu-704-upgrade-first-impressions/]("http://technical-itch.co.uk/2007/04/20/ubuntu-704-upgrade-first-impressions/")
[*] Manuel Amador Briz, at Rudd-O.com, has published an interview with author of Upstart, Scott James Remnant. Upstart is a replacement for init daemon which handles starting of tasks and services during boot, stopping them during shutdown and supervising them while the system is running. Read more at: [ http://rudd-o.com/archives/2007/04/24/interview-with-scott-ubuntu-and-upstart-developer/]("http://rudd-o.com/archives/2007/04/24/interview-with-scott-ubuntu-and-upstart-developer/")
[*] Todd Barnett, at gonnaeatthat.net, discusses how to convert Windows users to Ubuntu. While the negative Vista press sends many users to Ubuntu, showing off the features and uses of Compiz can attract lots of attention. Potential converts should be shown Linux equivalents of their Windows applications, like Evolution, Thunderbird, Gimp, and Open Office. Coverting users also requires commitment since they will inevitably ask for help. Todd has many other recommendations, such as setting up bookmarks to reference guides and ubuntuguide.org, and teaching basic shell commands. Read more at: [ http://www.gonnaeatthat.net/2007/04/27/how-to-convert-windows-users-to-ubuntu/]("http://www.gonnaeatthat.net/2007/04/27/how-to-convert-windows-users-to-ubuntu/")[/LIST][SIZE=5]**Meetings and Events**[/SIZE]

    **Tuesday, May 1, 2007**

   **Kernel Team Meeting**[LIST]
[*] Start: 15:00
[*] End: 16:00
[*] Location: IRC channel #ubuntu-meeting
[*] Agenda: [ https://wiki.ubuntu.com/KernelTeam/Meeting]("https://wiki.ubuntu.com/KernelTeam/Meeting")[/LIST]**Mozilla Team Meeting**[LIST]
[*] Start: 18:00
[*] End: 20:00
[*] Location: IRC channel #ubuntu-meeting
[*] Agenda: [ https://wiki.ubuntu.com/MozillaTeam/Meetings]("https://wiki.ubuntu.com/MozillaTeam/Meetings")[/LIST]**Wednesday, May 2, 2007**

   **Edubuntu Meeting**[LIST]
[*] Start: 12:00
[*] End: 14:00
[*] Location: IRC channel #ubuntu-meeting
[*] Agenda: [ https://wiki.edubuntu.org/EdubuntuMeetingAgenda]("https://wiki.edubuntu.org/EdubuntuMeetingAgenda")[/LIST]**Xubuntu Developers Meeting**[LIST]
[*] Start: 20:00
[*] End: 22:00
[*] Location: IRC channel #ubuntu-meeting
[*] Agenda: [ https://wiki.ubuntu.com/Xubuntu/Meetings]("https://wiki.ubuntu.com/Xubuntu/Meetings")[/LIST]**Thursday, May 3, 2007**

   **Ubuntu Education Summit**[LIST]
[*] End: 23:59
[*] Location: Sevilla, Spain
[*] Wiki page: [ https://wiki.ubuntu.com/UES-Sevilla]("https://wiki.ubuntu.com/UES-Sevilla")[/LIST]**Ubuntu Development Team Meeting**[LIST]
[*] Start: 16:00
[*] End: 18:00
[*] Location: IRC channel #ubuntu-meeting[/LIST]**Friday, May 4, 2007**

   **Ubuntu Education Summit**[LIST]
[*] End: 23:59
[*] Location: Sevilla, Spain
[*] Wiki page: [ https://wiki.ubuntu.com/UES-Sevilla]("https://wiki.ubuntu.com/UES-Sevilla")[/LIST]**Saturday, May 5, 2007**

   **Ubucon - Sevilla, Spain**[LIST]
[*] Start: 10:00/Madrid, 08:00/GMT
[*] End: 17:30/Madrid, 15:30/GMT
[*] Location: University of Seville, Sevilla, Spain
[*] Wiki page: [ https://wiki.ubuntu.com/TheUbucon/Sevilla]("https://wiki.ubuntu.com/TheUbucon/Sevilla")[/LIST][SIZE=5]**Updates and security for 6.06, 6.10, and 7.04**[/SIZE]

   **Security Updates**[LIST]
[*] USN-454-1: PostgreSQL vulnerability - [ http://www.ubuntu.com/usn/usn-454-1]("http://www.ubuntu.com/usn/usn-454-1")
[*] USN-455-1: PHP vulnerabilities - [ http://www.ubuntu.com/usn/usn-455-1]("http://www.ubuntu.com/usn/usn-455-1")
[*] USN-453-2: rdesktop regression - [ http://www.ubuntu.com/usn/usn-453-2]("http://www.ubuntu.com/usn/usn-453-2")[/LIST]**Ubuntu 6.06 LTS Updates**[LIST]
[*] lighttpd 1.4.11-3ubuntu3.0.1 - [ https://lists.ubuntu.com/archives/dapper-changes/2007-April/012412.html]("https://lists.ubuntu.com/archives/dapper-changes/2007-April/012412.html")
[*] rdesktop 1.4.1-1.1ubuntu0.6.06 - [ https://lists.ubuntu.com/archives/dapper-changes/2007-April/012413.html]("https://lists.ubuntu.com/archives/dapper-changes/2007-April/012413.html")
[*] php5 5.1.2-1ubuntu3.7 - [ https://lists.ubuntu.com/archives/dapper-changes/2007-April/012414.html]("https://lists.ubuntu.com/archives/dapper-changes/2007-April/012414.html")
[*] postgresql-8.1 8.1.9-0ubuntu0.6.06 - [ https://lists.ubuntu.com/archives/dapper-changes/2007-April/012415.html]("https://lists.ubuntu.com/archives/dapper-changes/2007-April/012415.html")
[*] mydns 1.1.0+pre-3ubuntu0.1 (source) - [ https://lists.ubuntu.com/archives/dapper-changes/2007-April/012416.html]("https://lists.ubuntu.com/archives/dapper-changes/2007-April/012416.html")[/LIST]**Ubuntu 6.10 Updates**[LIST]
[*] update-manager 0.45.4 - [ https://lists.ubuntu.com/archives/edgy-changes/2007-April/008316.html]("https://lists.ubuntu.com/archives/edgy-changes/2007-April/008316.html")
[*] k3d 0.5.12.0-1ubuntu2.1~proposed2 - [ https://lists.ubuntu.com/archives/edgy-changes/2007-April/008317.html]("https://lists.ubuntu.com/archives/edgy-changes/2007-April/008317.html")
[*] lighttpd 1.4.13~r1370-1ubuntu1.1 - [ https://lists.ubuntu.com/archives/edgy-changes/2007-April/008318.html]("https://lists.ubuntu.com/archives/edgy-changes/2007-April/008318.html")
[*] rdesktop 1.4.1-1.1ubuntu0.6.10 - [ https://lists.ubuntu.com/archives/edgy-changes/2007-April/008319.html]("https://lists.ubuntu.com/archives/edgy-changes/2007-April/008319.html")
[*] postgresql-8.1 8.1.9-0ubuntu0.6.10 - [ https://lists.ubuntu.com/archives/edgy-changes/2007-April/008320.html]("https://lists.ubuntu.com/archives/edgy-changes/2007-April/008320.html")
[*] php5 5.1.6-1ubuntu2.4 - [ https://lists.ubuntu.com/archives/edgy-changes/2007-April/008321.html]("https://lists.ubuntu.com/archives/edgy-changes/2007-April/008321.html")
[*] mydns 1:1.1.0-3ubuntu0.1 - [ https://lists.ubuntu.com/archives/edgy-changes/2007-April/008322.html]("https://lists.ubuntu.com/archives/edgy-changes/2007-April/008322.html")[/LIST]**Ubuntu 7.04 Updates**[LIST]
[*] cinepaint 0.21-2-0ubuntu4.1~proposed1  - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008563.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008563.html")
[*] apport 0.76.1~prop1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008564.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008564.html")
[*] tzdata 2007e-0ubuntu0.7.04~prop1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008565.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008565.html")
[*] update-manager 1:0.59.21 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008566.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008566.html")
[*] control-center 1:2.18.1-0ubuntu2.1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008567.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008567.html")
[*] rdesktop 1.5.0-1ubuntu1~prop1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008568.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008568.html")
[*] gnome-panel 1:2.18.1-0ubuntu3.1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008569.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008569.html")
[*] tzdata 2007e-0ubuntu0.7.04 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008570.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008570.html")
[*] bughelper 0.1.13.1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008571.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008571.html")
[*] k3d 0.6.6.0.ds1-1ubuntu0.1~proposed1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008572.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008572.html")
[*] postgresql-8.2 8.2.4-0ubuntu0.7.04 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008573.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008573.html")
[*] php5 5.2.1-0ubuntu1.1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008574.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008574.html")
[*] rdesktop 1.5.0-1ubuntu1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008575.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008575.html")
[*] apport 0.76.1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008576.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008576.html")
[*] mydns 1:1.1.0-6ubuntu0.1 - [ https://lists.ubuntu.com/archives/feisty-changes/2007-April/008577.html]("https://lists.ubuntu.com/archives/feisty-changes/2007-April/008577.html")[/LIST][SIZE=5]**Bug Stats**[/SIZE][LIST]
[*] Open (28906) +776 # over last week
[*] Critical (22) +4 # over last week
[*] Unconfirmed (14089) +344 # over last week
[*] Unassigned (21550) +670 # over last week
[*] All bugs ever reported (97295) +1653 # over last week[/LIST]As always, the Bug Squad needs more help. If you want to get started, please see [ https://wiki.ubuntu.com/HelpingWithBugs]("https://wiki.ubuntu.com/HelpingWithBugs") 
 Check out the bug statistics: [ http://people.ubuntu-in.org/~carthik/bugstats/]("http://people.ubuntu-in.org/%7Ecarthik/bugstats/")  
  [B]
[SIZE=5]Archives and RSS Feed[/SIZE][/B]

  You can always find older Ubuntu Weekly Newsletter issues at: [ https://wiki.ubuntu.com/UbuntuWeeklyNewsletter]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter") 
 
You can subscribe to the Ubuntu Weekly News via RSS at: [ http://fridge.ubuntu.com/uwn/feed]("http://fridge.ubuntu.com/uwn/feed")

[SIZE=5]**Additional Ubuntu News**[/SIZE]

  As always you can find more news and announcements at:[LIST]
[*][ http://www.ubuntu.com/news]("http://www.ubuntu.com/news")[/LIST]and[LIST]
[*][ http://fridge.ubuntu.com/]("http://fridge.ubuntu.com/")[/LIST][SIZE=5]**RSS**[/SIZE]

  You can suscribe to the UWN feed at: [ http://fridge.ubuntu.com/uwn/feed]("http://fridge.ubuntu.com/uwn/feed") 
  [B]
[SIZE=5]Feedback[/SIZE][/B]

  This document is maintained by the Ubuntu Marketing Team. Please feel free to contact us regarding any concerns or suggestions by either sending an email to [EMAIL="ubuntu-marketing@lists.ubuntu.com"][IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/u-email.png[/IMG] ubuntu-marketing@lists.ubuntu.com[/EMAIL] or by using any of the other methods on the Ubuntu Marketing Team Contact Information Page ([ https://wiki.ubuntu.com/MarketingTeam]("https://wiki.ubuntu.com/MarketingTeam")). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please send then [EMAIL="ubuntu-users@lists.ubuntu.com"][IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/u-email.png[/IMG] ubuntu-users@lists.ubuntu.com[/EMAIL].

[SIZE=5]**Credits**[/SIZE]

The Ubuntu Weekly Newsletter is brought to you by:[LIST]
[*]Martin Albisetti
[*]Nick Ali
[*]Gabriele Monti
[*]Corey Burger
[*]And many others[/LIST]

---

### Post by revertex on 2007-05-02
wow! these fonts are really [SIZE=5]HUGE[/SIZE]!

---

### Post by Jenda on 2007-05-08
There, I toned them down a bit &#12484;

---

### Post by Vorian on 2007-05-08
:(

---

