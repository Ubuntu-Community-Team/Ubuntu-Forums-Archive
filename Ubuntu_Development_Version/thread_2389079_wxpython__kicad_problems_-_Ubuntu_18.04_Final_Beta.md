---
title: "wxpython / kicad problems - Ubuntu 18.04 Final Beta + updates"
date: 2018-04-11
forum: Ubuntu Development Version
---

### Post by tsrdel88 on 2018-04-11
Hello,

I'd like to report some problems with kicad / wxpython combination in current 18,04. 
The problem is in compatibility of wxpython and libwxgtk packages used for kicad compilation. So.. kicad from one side is compiled against libwxgtk3.0-0v5, which includes WxGtk version 3.0 compiled with **gtk2** and from other side uses  wxpython from package python-wxgtk3.0 compiled with WxGtk version 3.0, which is compiled with **gtk3.**This doesn't work and when one runs pcbnew from kicad following error appears:
"../src/common/object.cpp(251): assert "classTable->Get(m_className) == NULL" failed in Register(): Class "wxCommandEvent" already in RTTI table - have you used IMPLEMENT_DYNAMIC_CLASS() multiple times or linked some object file twice)?", which is typical error of double loading different WxGtk library versions in the same application.

Sorry, that I don't report the bug in launchpad, but when I try to log into launchpad with my chromium and ubuntu one accound it doesn't work ( second bug in my report ) with following description of error: [h=1]"Oops![/h][COLOR=#333333][FONT=Ubuntu]Sorry, something just went wrong in Launchpad.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]We’ve recorded what happened, and we’ll fix it as soon as possible. Apologies for the inconvenience.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu](Error ID: OOPS-41948cdcc9c9af3a870a34516bc57cd9)"

I see some inconsistancy with the naming of packages in 18.04:
libwxgtk3.0-0v5 - contains WxGtk compiled with [B]gtk2
[/B]libwxgtk3.0-gtk3-0v5 - contains WxGtk compiled with **gtk3**, but....
python-wxgtk3.0 - contains wxpython compiled with WxGtk for [B]gtk3
[/B]Maybe it would be useful ( or even required ) to split wxpython into two package series: 
python-wxgtk3.0-xxxx - with packages for WxGtk compiled with ** gtk2 **and
python-wxgtk3.0-gtk3-xxx  - with packages for WxGtk compiled with [B]gtk3
[/B]This way is would be at least consistant. 
I don't know if it is possible to install wxpython for various wxgtk version parallel in the system, but I hope it is possible - otherwise keeping packages with various wxpython dependancies would be PITA,

regards,

T.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
[LIST]
[/LIST]
[/FONT][/COLOR]

---

### Post by dino99 on 2018-04-11
hello,

you are here into ubuntuforums, the place to discuss about dev release and LTS.
To report an issue, open a terminal and run "ubuntu-bug  yourfaultypackagename"

About kicad, the version 4.07 is found into the bionic archive, and ready to use (already compiled).
As you complain about 'compilation', then you should post into that subforum, not here.

---

### Post by PaulW2U on 2018-04-11
> **tsrdel88 said:**
> Sorry, that I don't report the bug in launchpad, but when I try to log into launchpad with my chromium and ubuntu one accound it doesn't work ( second bug in my report ) with following description of error: 

"Oops! Sorry, something just went wrong in Launchpad.
We’ve recorded what happened, and we’ll fix it as soon as possible. Apologies for the inconvenience.
(Error ID: OOPS-41948cdcc9c9af3a870a34516bc57cd9)"
That message will go away once the Launchpad admins have fixed whatever is wrong. Whenever you see this message, wait a few minutes and try again.

---

### Post by dino99 on 2018-04-11
Related [https://bugs.launchpad.net/kicad/+bug/1762432](https://bugs.launchpad.net/kicad/+bug/1762432)

---

### Post by jbicha on 2018-04-11
See if the [new kicad]("https://launchpad.net/ubuntu/+source/kicad") that will show up in today's updates fixes your issue.

---

### Post by tsrdel88 on 2018-04-12
> **PaulW2U said:**
> That message will go away once the Launchpad admins have fixed whatever is wrong. Whenever you see this message, wait a few minutes and try again.

Right now I've tried to issue a command "ubuntu-bug kicad", but what I've seen is once again 
"[h=1]Oops![/h][COLOR=#333333][FONT=Ubuntu]Sorry, something just went wrong in Launchpad.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]We’ve recorded what happened, and we’ll fix it as soon as possible. Apologies for the inconvenience.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu](Error ID: OOPS-9722d06157cd3e66fbc985bf8af1da70)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]"
I have tried to do the same on 16.04 and it also doesn't work. So we get to the point:  where one should report problems with bug reporting system?

regards,

T.
[LIST]
[/LIST]
[/FONT][/COLOR]

Ps. kicad works better - at least pcbnew can run, but default view doesn't work, so there are still some bugs to be reported.

---

### Post by PaulW2U on 2018-04-12
> **tsrdel88 said:**
> I have tried to do the same on 16.04 and it also doesn't work. So we get to the point:  where one should report problems with bug reporting system?
I'm not sure what the problem is as I've just tried to report a bug for both gnome-terminal and kicad and I'm not seeing any errors. Obviously I haven't finished the reporting process as I've no bug to report.

Have you registered at Launchpad itself? I'm not sure having a just an Ubuntu One login is enough. If you go to [https://launchpad.net/](https://launchpad.net/), do you see your name in the top  right corner of the screen or "Log in/Register"?

Edit: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) says that a Launchpad account is required in order to report a bug.

---

### Post by jbicha on 2018-04-12
Launchpad has recurring timeout issues. I suggest just trying again later. Sorry.

But see my comment earlier that there is a new kicad update in Ubuntu 18.04.

---

### Post by tsrdel88 on 2018-04-12
I cannot login with my ubuntu one account to launchpad.net at all - it doesn't matter if I am trying to report bugs, or simply try to press log in/register top-right when in the launchpad.net main page and accepting giving out credentials from ubuntu one. I haven't logged in any single time - every time I see the message I've written. 
Concerning kicad: yes, I've tried version 4.0.7+dfsg1-1ubuntu2 and the bug I've tried to report is gone ( pcbnew runs ), but want to report another bug: default view in pcbnew doesn't work ( although opengl and cairo seem to work fine ),

regards,

T.

---

### Post by dino99 on 2018-04-12
you can try:
- loging with an other browser (chromium/firefox)
- try an other user session

indeed that needs a valid 'one account' id
[https://ubuntuforums.org/showthread.php?t=2230004](https://ubuntuforums.org/showthread.php?t=2230004)

---

### Post by tsrdel88 on 2018-04-13
I have set second account in ubuntu one up and this time I can log in to launchpad without glitch. With the second one it is not possible. I don't have a clue why it works with one account and doesn't with second one. 
Thanks for your help anyway,

Regards, T.

---

### Post by davidsrsb on 2018-05-06
On release 18.04 with 4.0.7 from the electronics repository, the cursor leaves ghost trails, making kicad unusable
This is a continuing problem due to wxpython and Gtk3

---

### Post by wildmanne39 on 2018-05-06
18.04 is no longer in development so thread closed!

Thanks for sharing!

---

