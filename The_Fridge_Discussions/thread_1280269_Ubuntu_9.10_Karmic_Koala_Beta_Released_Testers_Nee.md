---
title: "Ubuntu 9.10 Karmic Koala Beta Released: Testers Needed!"
date: 2009-10-01
forum: The Fridge Discussions
---

### Post by TheFridge on 2009-10-01
Like everyone else with their heart invested in Ubuntu, I am tickled pink to see that [Ubuntu 9.10 Karmic Koala Beta]("http://www.ubuntu.com/testing/karmic/beta") has been released. Our global community of contributors and developers has worked tirelessly to get this Beta out, and there are lots of great features in there including Upstart switched on by default, improved boot experience, the new Ubuntu Software Center, new messaging indicator changes, and lots of EC2 and Ubuntu Enterprise Cloud awesomeness. You can download the furry little blighter here.

 But wait…before you go and download it…I want to talk about the point of a beta…it is, in a word…

 [CENTER][IMG]http://farm3.static.flickr.com/2597/3972425227_9343f975b1_o.jpg[/IMG][/CENTER]

 Unfortunately, nestled inside all of the lovelyness I described are some inevitable bugs. While we have an incredible bunch of people at Canonical and in the community that fix bugs, we are really looking to you good people to hunt these bugs down and report them so we (a) know about them and can (b) fix them and make Ubuntu the best Operating System it can be.

 Of course, the whole system needs testing, but there are some key topics which some of us in the Ubuntu land would like you to give a solid test to. It is these features which are new to Ubuntu and need the most love and attention. So, let’s cover them…

 **Empathy Audio and Video Calls**

 Karmic ships with a new instant messaging client called Empathy, based on the tremendous Telepathy framework. Empathy is the right direction for IM in the GNOME and Ubuntu projects, and recent additions to it include screen sharing and audio and video calling. The audio/video side of Empathy has had some mixed results for different users, so this really needs your love.

 This is how you test:

 First, run Empathy from Applications->Internet->Empathy IM Client. Next add a Google Talk or Jabber account. If you see a contact with a microphone or video camera next to their name, right click them and click Audio Call or Video Call. It should call them, they will then accept the call and you can have an audio or video chat.

 If this doesn’t work as expected, open up a terminal Applications->Accessories->Terminal and type in

 ubuntu-bug empathy

 Follow the instructions to file your bug. You can check to see if your bug has already been filed by looking at the [Empathy Bugs List]("https://bugs.edge.launchpad.net/ubuntu/+source/empathy/").

 Another really useful thing you can do if you face problems is to first quit Empathy and then in the terminal type:

 EMPATHY_LOGFILE=/tmp/empathy.log GST_DEBUG=\*fsrtp\*:5 EMPATHY_DEBUG=all empathy

 This generates a log file and you should then attach the empathy.log file in the /tmp directory to the bug report.

 **Boot Experience**

 Karmic introduces a faster and more beautiful boot experience, but we are still trying to weed out some bugs here and there.

 Testing this is simple: boot your system and after you see a message about GRUB loading, you shouldn’t see any other messages before you see the Ubuntu logo on a gray background. If you do see messages, you have found a bug.

 We need you to let us know what the text says so we can eliminate the message from the boot process. There are a few ways you can do this:

 
[LIST] 
[*]When you are logged into the desktop, use Ctrl-Alt-1 to flick to VT1 and see if the messages are there. If so, note them down or take a photo of the screen in which you can see the text clearly.Another approach is to remember a word or two from the boot message and then click System->Administration->Log File Viewer and click on either the dmesg or syslog entries and use Ctrl-F to search for the text you remembered. If you then see it, add that to a bug report. 
[/LIST]
 If you think the bug is a kernel bug (typically when the message refers to a device or driver on your system), open up a terminal Applications->Accessories->Terminal and type in

 ubuntu-bug linux

 If you find that the gray graphic with the Ubuntu logo that shows while Ubuntu is loading doesn’t behave as you expect, run this command to report the bug:

 ubuntu-bug xsplash

 Finally, if you are having problems with the graphical login prompt, run this:

 ubuntu-bug gdm

 When you have filed your bug, view the bug report in your web browser, and under Bug Description there is a Tags line. Click the small yellow circle with a ‘!’ inside it and add the tag ubuntu-boot-experience. This will help our developers to find it and do their best to fix it.

 **EC2**

 All new Ubuntu releases (including Alphas and Betas) are now available as Amazon EC2 images. Thanks to the stunning work of Ara Pulido and Scott Moser, we have a great set of tests you can run to test out these images. First go and [read this starters guide to EC2 and Ubuntu]("https://help.ubuntu.com/community/EC2StartersGuide") and then [try the tests out here]("https://wiki.ubuntu.com/Testing/EC2/TestCases"). You can leave your feedback on [this wiki page]("https://wiki.ubuntu.com/Testing/EC2/Results") and file bugs [here]("https://bugs.edge.launchpad.net/ubuntu-ami-testing").

 **Getting Help**

 If you have any questions or queries about testing and filing bugs, here are some resources:

 
[LIST] 
[*][Reporting Bugs]("https://help.ubuntu.com/community/ReportingBugs") – this page provides more detail about how to file a bug with ubuntu-bug and other tools.[General Testing Team Documentation]("https://wiki.ubuntu.com/Testing") – there is lots of help here on these pages about how to help with testing Ubuntu. 
[/LIST]
 A great place to get is IRC too, in these channels (all on the Freenode IRC network):

 
[LIST] 
[*]#ubuntu-bugs
[*]#ubuntu-quality
[*]#ubuntu-release#ubuntu-testing 
[/LIST]
 Thanks again for taking part in testing Ubuntu and in helping to make it as great as possible!

 Originally posted by Jono Bacon [here]("http://www.jonobacon.org/2009/10/02/ubuntu-9-10-karmic-koala-beta-released-testers-needed/") on Friday, October 2nd, 2009 at 12:59 am

 

[More...](http://fridge.ubuntu.com/node/1920)

---

