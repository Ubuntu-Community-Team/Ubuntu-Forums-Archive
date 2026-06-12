---
title: "[3D] VirtualBox guests abort on switching to full-screen mode"
date: 2013-07-08
forum: Virtualisation
---

### Post by twipley on 2013-07-08
EDIT: a thread concerning this the side of the VirtualBox boards: [https://forums.virtualbox.org/viewtopic.php?f=7&t=56338&p=261004](https://forums.virtualbox.org/viewtopic.php?f=7&t=56338&p=261004)

It seems all of a sudden (because of recent Ubuntu updates?) there is a crashing problems when going fullscreen with 3D additions enabled.

I know I am not alone experiencing this issue. Please post the last thing you did before it was not working anymore (e.g., updating VirtualBox, or updating your specific Ubuntu distro), so we can determine the source of the problem.


Personally, 4.2.14 was working fine, and upon performing some Linux Mint updates, 3D applications under guests would not be starting anymore without the guest aborting. Switching to fullscreen mode now produces the same effect, too.

---

### Post by gwm on 2013-07-08
I can't say exactly when it started happening other than very recently.
It seems to me that my symptoms are a little different because I turned off 3D by coincidence when trying to find out why the guest OS crashed when changing to or from full screen.

Mine was starting in full screen because of last time and would crash when trying to come out of it.

In the guest, I would run a program that opened multiple Windows and when I tried to close a window the whole guest OS would hang. However, it didn't hang permanently. If I left it and went away to do something else, I would find the window closed when I came back later. Hence I was blaming the guest OS. Then when I tried to move the hanging guest OS out of full screen mode it would abort instantly.

Still, I have found something else that may help.

When I execute a **Wine application** from within Ubuntu, all is well until I attempt to close the application.
I click on the close button in the command box and nothing happens other than some changes in coloring. The color change means to me that the application has been informed of the mouse click event via Wine. Yet the action to close the program down has not worked. Just to spoil my theory, Alt-F4 terminates the Wine application correctly.
Something about the propagation of events up and down the chain has gone wrong.

I take it that both VBox and Wine intercept events by inserting themselves into the interrupt chain or whatever terminology modern programmers use for such things. Perhaps some of these chains have been modified by recent kernel updates and now the return to the kernel interrupt handler is somehow failing. In some cases it returns benignly to some random spot in the code but leaves interrupts disabled. In other cases, it returns to something wierd and crashes.

[3D] VirtualBox guests abort on switching to full-screen mode seems to be fixed by reinstalling guest additions.

At any rate, in the last 24h, I have received a whole bunch of Windows and Ubuntu updates. I am now running with 3D turned on and the guest OS nolonger crashes.

The windows updates seemed to clear my problem with individual windows taking exeptionally long times to close. However, the guest OS, Windows7, still takes half an hour (not exagerating) to close. I started a shut down before coming on line to the forum and it has still not shut down. This is a fast PC and it normally takes less than 10s to close the guest OS.

---

