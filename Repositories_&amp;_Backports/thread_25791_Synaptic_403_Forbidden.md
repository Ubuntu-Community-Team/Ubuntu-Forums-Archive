---
title: "Synaptic: 403 Forbidden?"
date: 2005-04-10
forum: Repositories &amp; Backports
---

### Post by fisheromen1031 on 2005-04-10
I'm having a problem with Synaptic today.  When I click the Reload button, I get a message and progress bar talking about downloading 38 files as usual.  After it gets up to 37 of 38, I get the following message.  

[INDENT]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/Packages.gz:](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/Packages.gz:) 403 Forbidden
[http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/binary-i386/Packages.gz:](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/binary-i386/Packages.gz:) 403 Forbidden
[/INDENT]

What does this mean?  I've never had this problem before.  btw, I haven't upgraded to Hoary yet. 

thanks,

fisher

---

### Post by Nis on 2005-04-10
The sourceforge repository for the Ubuntu backports has been disabled since April 1st.  Check [here](http://backports.ubuntuforums.org/) for information on what to replace the old repository information with.

---

### Post by fisheromen1031 on 2005-04-11
Thanks a whole bunch!!!!

 \\:D/

---

### Post by jdong on 2005-04-11
Yep -- knew that there's still people using the old Backports repo. Over the weekend, I chmodded everything to 700 @ sourceforge, to make it more obvious that you need to move on!

Going to [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) automatically redirects you to information about the new Backports repo, so I thought it's pretty smooth of an upgrade.

---

### Post by nashife on 2005-04-13
I've tried to follow the instructions, adding a line that says "deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe" and commenting out the old backports line....

However, I get the following error when I try to open Synaptic: "Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_warty-backports_main_binary-i386_Packages) - stat (2 No such file or directory)"

(I get an error for both the main and the universe)

What does this mean?  what's with those underscores in the error?

sorry in advance if this is a stupid question...

---

### Post by jdong on 2005-04-13
That means you need to reload the list, or do an apt-get update.

---

