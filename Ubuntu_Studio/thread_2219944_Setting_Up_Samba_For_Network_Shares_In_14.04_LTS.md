---
title: "Setting Up Samba For Network Shares In 14.04 LTS ?"
date: 2014-04-26
forum: Ubuntu Studio
---

### Post by kg4muc on 2014-04-26
I am having a bit of a problem with getting some network files shared.
First of all I have down loaded SAMBA and have assigned passwords
and also under the desired folders to share properties tab I have set the 
permissions for SAMBA SHARE.

Question is what have I missed?
Other than this I have Ubuntu Studio running in the recording studio
with really good results! At least when I learn the in's and out's of Linux
I will not be tied to WIN and the rediculous prices of some of the plug ins
there :)

To recap.. I have did all the above but the computer doesn't show up on the network
and if it shows on other "Nix" clients I can't access the folders shared.


Thanks in advance for any and all help!


Wayne

---

### Post by david-daking on 2014-06-29
I had the same problem, there is a Shared Folders program in System on the Menu and it did not do anything when I tried to add a folder to share. Samba was already installed.

Then I installed system-config-samba and gadmin-samba via Synaptic.

Now from the main menu, System, I see Samba there. I opened that and it allowed me to add shared folders, and another Linux PC on the network could now see the shared folder.

---

### Post by gordintoronto on 2014-06-29
How did you set up the shares? I do it from Nautilus, and it has never been a problem.

Just as a test, set up a wide-open share. To create a shared folder on any distro which uses Nautilus as its file manager, I create a folder called "shared". In Nautilus, I right-click and select click on "sharing options." I click on "Share this folder," "Allow others to create and delete files in this folder", and "Guest access." Then I click on "Create Share." All done.

---

