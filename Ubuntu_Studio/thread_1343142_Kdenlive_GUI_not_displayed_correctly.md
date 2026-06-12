---
title: "Kdenlive GUI not displayed correctly"
date: 2009-12-01
forum: Ubuntu Studio
---

### Post by ArielEnter on 2009-12-01
I being trying Kdenlive, but I got a problem. The user interface is not displayed correctly as showed in this two pictures. Picture number one show how it looks in my computer and number two shows how it should look. As you can see, many graphic guides are not being displayed, like the border of the transition and the position of picture to picture transition.
 

 I have the visual effects to “None”. My computer is a MacBook 4.1 which has an Intel [GMA]("http://guides.macrumors.com/index.php?title=GMA&action=edit") X3100 graphic card with 144 MB shared memory. I'm using Ubuntu 9.10 Karmic.
 

 I first installed the version available in the repositories 7.5-1 and I had the same problem. Then I follow the instructions available in the Kdenlive website and got the the 7.6 from sunab alternative repositories.
 

 I also installed kdenlive in a virtualbox's virtual installation of karmic and it worked fine.
 

 Can anybody help me with this problem?

---

### Post by ArielEnter on 2009-12-02
The solution is shown here [http://kdenlive.org/mantis/view.php?id=1246](http://kdenlive.org/mantis/view.php?id=1246) thanks to [j-b-m]("http://www.kdenlive.org/users/j-b-m") from the kdenlive forums for his grateful help.

Is a problem involving the  intel video driver.

The way it worked for me is the following:

I used xorg-edgers' drivers-only repository, by going to System>>Administration>> Synaptic Package Manager. Then on the menu Settings>>Repositories. Go to the Other Software tab, click the add button and write ppa:xorg-edgers/drivers-only. Then close the window and push Reload button back on Synaptic Package Manager. At last, you click on Mark all updates and Apply. Reboot your system and that's it.

This will update not only xserver-xorg-video-intel but some other drivers as well. I guess that's what made xserver-xorg-video-intel work fine on my computer.

---

