---
title: "Guidance on new server storage"
date: 2012-04-26
forum: Server Platforms
---

### Post by drexlock on 2012-04-26
[COLOR=black][FONT=Verdana]I've had what some may say is good and bad luck recently. I arrived home from work the other day to find the Raid card in my server had bit the dust and took my OS along with it. Now I didn’t lost any data (thanks to my data paranoid backups) and low and behold Ubuntu 12.04 was released today so now I have a legitimate excuse to build a new box![/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]My big stumbling block is server storage. Hardware raid was to be honest quiet easy to setup and once it was done it was up and running it was set, but with the last card dying I’m a little leery about going that route again. Everyone on the forums seems to sing the praises of mdadm but I am not really familiar with using the command line (coming from a mostly windows house). I have a Drobo S (USB3) that I could use but I want to keep everything in one box as much as possible.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]My overall goal with this new machine is to have three Raid Arrays. One Raid1 for my boot drive, one Raid1 for VMs (using KVM or Virtualbox) and one 4 disk Raid5 for server shares and storage. The big thing I’m looking for is to have the Raid5 have the expandability and upgradability of the DroboS but keep everything internal in one machine. Is this even possible? And on a side note is there a GUI of some kind for mdadm for managing Arrays?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thanks for any help you can provide![/FONT][/COLOR]

---

