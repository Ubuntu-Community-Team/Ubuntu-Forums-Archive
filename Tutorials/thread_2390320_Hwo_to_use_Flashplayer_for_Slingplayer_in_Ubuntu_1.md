---
title: "Hwo to use Flashplayer for Slingplayer in Ubuntu 18.04"
date: 2018-04-27
forum: Tutorials
---

### Post by Herber on 2018-04-27
If you want to use slingplayer in Ubuntu 18.04 you will need Flashplayer to work in Firefox.  I am not good at making screenshots but here is a tutorial for how to make Flashplayer work.

     1) Enable Canonical partners in the "Software and Uupdates" application.  Do this by checking the box in the canonical partners heading under the "Other Software" tab.

     2) Update Sources:
           i.e.  " sudo apt-get update"

     3) Install flashplayer plugin installer:
          i.e.  " sudo apt-get install flashplugin-installer"

     
     4) Install The pepperflash browser plugin:
          i.e.  "sudo apt-get install browser-plugin-freshplayer-pepperflash"
 
     5) Download and extract the up to date .tar from Adobe's website.
          A) Download and save .tar file to your Downoads folder.
          B) in terminal go to Downloads Folder.  ie. " cd Downloads"
          C) In Downloads Folder Extract the .tar file.  ie. " tar -xvf "adobefile".tar"

     6) Now there will be a file in your Downloads folder named   "something".so   find it in terminal by using the "ls" command while in your Downloads folder.  The last step is to move this file from your Downloads folder to /usr/lib/mozilla/plugins.  To move this file you need to have root privileges.

     7) To gain root privileges for this operation:
          A) open a terminal and start nautilus in root by typing " sudo nautilus"
          B) open a second instance of root nautilus by opening a second terminal and typing " sudo nautilus" again.
          C) Navigate in one nautilus instance to your "Downloads" folder.
          D) Navigate in the other nautilus instance to your "usr/lib/mozilla/plugins" folder.
          E) Drag and drop the file you extracted from the "adobe".tar file with the name "something".so (in you Downloads folder) to the "usr/lib/mozilla/plugins" folder.
          F) You are now ready to use flashplayer in firefox with Ubuntu 18.04.

     8) To view and operate you slingbox in Ubuntu 18.04.
          A) open firefox and put this address into the address bar "slingplayer.slingbox.com/embedded/slingplayer.php" you will need to give permision to open flashplayer and then sign into your Slingbox account and voila you can use your slingbox in ubutu 18.04.  :D

---

