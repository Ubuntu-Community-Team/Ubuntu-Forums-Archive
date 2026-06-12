---
title: "Libre Office freezes after several minutes"
date: 2012-08-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Wise Ferret on 2012-08-26
Using 64-bit, nvidia proprietary driver on a gnome-classic session.

After several minutes of work, libre office freezes. Its window is not updated, and dragging it around fills it with garbage. It does not respond when I try to close it with mouse or keyboard (not even a system message about an unresponsive app), and I have to kill it from the terminal. I tried disabling hardware acceeleration in the preferences, but the problem remained.

Interestingly, cpu usage is normal, and there is no error message when I start soffice.bin from CLI. This is not related to the cpu hogging reported in an [earlier thread]("http://ubuntuforums.org/showthread.php?t=2047610") concerning unity-panel-service (which is not running in gnome-classic).

Any ideas?

---

### Post by dino99 on 2012-08-26
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1041865](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1041865)

---

### Post by Wise Ferret on 2012-08-26
> **dino99 said:**
> [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1041865](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1041865)

I think that this is not the problem I describe. My Libre Office freezes, not crashes; also, there is no excessive usage of ram or cpu.

EDIT: 
Actually I do see now a CPU spike. I missed it earlier. So this may indeed be the relevant bug.

---

### Post by vasa1 on 2012-08-26
> **Wise Ferret said:**
> ...
Any ideas?
OS and LibO version numbers? Calc, Writer, Draw, etc?

---

### Post by Wise Ferret on 2012-08-26
> **vasa1 said:**
> OS and LibO version numbers? Calc, Writer, Draw, etc?

QQ, with the standard versions in the repos (6.0~rc4-0ubuntu3).
But I do notice now a cpu spike I missed earlier, so it might be the aforementioned bug.

---

### Post by ajgreeny on 2012-08-26
Start the application in terminal, eg```
libreoffice --writer 
```so that when it freezes there may be an error showing in the terminal.

---

### Post by Wise Ferret on 2012-08-26
This is all I get, immediately on start up:

```
yotam@aku:~$ libreoffice --writer
Warning: failed to read path from javaldx
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
`menu_proxy_module_load': /usr/lib/libreoffice/program/soffice.bin: undefined symbol: menu_proxy_module_load

(soffice:9430): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/libreoffice/program/soffice.bin: undefined symbol: menu_proxy_module_load

(soffice:9430): Gtk-WARNING **: Failed to load type module: (null)

Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected
g_lo_action_group_set_action_enabled - .uno:AddDirect
g_lo_action_group_set_action_enabled - .uno:RecentFileList
g_lo_action_group_set_action_enabled - .uno:AutoPilotMenu
g_lo_action_group_set_action_enabled - .uno:ObjectMenue
g_lo_action_group_set_action_enabled - .uno:AvailableToolbars
g_lo_action_group_set_action_enabled - .uno:InsertPageHeader
g_lo_action_group_set_action_enabled - .uno:InsertPageFooter
g_lo_action_group_set_action_enabled - .uno:SetLanguageSelectionMenu
g_lo_action_group_set_action_enabled - .uno:SetLanguageParagraphMenu
g_lo_action_group_set_action_enabled - .uno:SetLanguageAllTextMenu
g_lo_action_group_set_action_enabled - .uno:ScriptOrganizer
p11-kit: duplicate configured module: gnome-keyring.module: /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
g_lo_action_group_set_action_enabled - .uno:AddDirect
g_lo_action_group_set_action_enabled - .uno:RecentFileList
g_lo_action_group_set_action_enabled - .uno:AutoPilotMenu
g_lo_action_group_set_action_enabled - .uno:Save
g_lo_action_group_set_action_enabled - .uno:SaveAll
g_lo_action_group_set_action_enabled - .uno:Reload
g_lo_action_group_set_action_enabled - .uno:VersionDialog
g_lo_action_group_set_action_enabled - .uno:SendOutlineToStarImpress
g_lo_action_group_set_action_enabled - .uno:SendOutlineToClipboard
g_lo_action_group_set_action_enabled - .uno:CreateAbstract
g_lo_action_group_set_action_enabled - .uno:SendAbstractToStarImpress
g_lo_action_group_set_action_enabled - .uno:Undo
g_lo_action_group_set_action_enabled - .uno:Redo
g_lo_action_group_set_action_enabled - .uno:Repeat
g_lo_action_group_set_action_enabled - .uno:Cut
g_lo_action_group_set_action_enabled - .uno:Copy
g_lo_action_group_set_action_enabled - .uno:SelectTextMode
g_lo_action_group_set_action_enabled - .uno:FieldDialog
g_lo_action_group_set_action_enabled - .uno:EditFootnote
g_lo_action_group_set_action_enabled - .uno:IndexEntryDialog
g_lo_action_group_set_action_enabled - .uno:AuthoritiesEntryDialog
g_lo_action_group_set_action_enabled - .uno:EditHyperlink
g_lo_action_group_set_action_enabled - .uno:LinkDialog
g_lo_action_group_set_action_enabled - .uno:ImageMapDialog
g_lo_action_group_set_action_enabled - .uno:CommentChangeTracking
g_lo_action_group_set_action_enabled - .uno:AvailableToolbars
g_lo_action_group_set_action_enabled - .uno:ShowAnnotations
g_lo_action_group_set_action_enabled - .uno:TaskPane
g_lo_action_group_set_action_enabled - .uno:InsertPageHeader
g_lo_action_group_set_action_enabled - .uno:InsertPageFooter
g_lo_action_group_set_action_enabled - .uno:InsertCaptionDialog
g_lo_action_group_set_action_enabled - .uno:RubyDialog
g_lo_action_group_set_action_enabled - .uno:RubyDialog
g_lo_action_group_set_action_enabled - .uno:EditRegion
g_lo_action_group_set_action_enabled - .uno:FrameDialog
g_lo_action_group_set_action_enabled - .uno:GraphicDialog
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToHalfWidth
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToHalfWidth
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToFullWidth
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToFullWidth
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToHiragana
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToHiragana
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToKatakana
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToKatakana
g_lo_action_group_set_action_enabled - .uno:SetAnchorToPage
g_lo_action_group_set_action_enabled - .uno:SetAnchorToPara
g_lo_action_group_set_action_enabled - .uno:SetAnchorAtChar
g_lo_action_group_set_action_enabled - .uno:SetAnchorToChar
g_lo_action_group_set_action_enabled - .uno:SetAnchorToFrame
g_lo_action_group_set_action_enabled - .uno:WrapOff
g_lo_action_group_set_action_enabled - .uno:WrapOn
g_lo_action_group_set_action_enabled - .uno:WrapIdeal
g_lo_action_group_set_action_enabled - .uno:WrapThrough
g_lo_action_group_set_action_enabled - .uno:WrapThroughTransparent
g_lo_action_group_set_action_enabled - .uno:WrapContour
g_lo_action_group_set_action_enabled - .uno:ContourDialog
g_lo_action_group_set_action_enabled - .uno:WrapAnchorOnly
g_lo_action_group_set_action_enabled - .uno:TextWrap
g_lo_action_group_set_action_enabled - .uno:CommonAlignTop
g_lo_action_group_set_action_enabled - .uno:CommonAlignVerticalCenter
g_lo_action_group_set_action_enabled - .uno:CommonAlignBottom
g_lo_action_group_set_action_enabled - .uno:BringToFront
g_lo_action_group_set_action_enabled - .uno:ObjectForwardOne
g_lo_action_group_set_action_enabled - .uno:ObjectBackOne
g_lo_action_group_set_action_enabled - .uno:SendToBack
g_lo_action_group_set_action_enabled - .uno:SetObjectToForeground
g_lo_action_group_set_action_enabled - .uno:SetObjectToBackground
g_lo_action_group_set_action_enabled - .uno:FlipHorizontal
g_lo_action_group_set_action_enabled - .uno:FlipVertical
g_lo_action_group_set_action_enabled - .uno:FormatGroup
g_lo_action_group_set_action_enabled - .uno:FormatUngroup
g_lo_action_group_set_action_enabled - .uno:EnterGroup
g_lo_action_group_set_action_enabled - .uno:LeaveGroup
g_lo_action_group_set_action_enabled - .uno:TransformDialog
g_lo_action_group_set_action_enabled - .uno:FormatLine
g_lo_action_group_set_action_enabled - .uno:FormatArea
g_lo_action_group_set_action_enabled - .uno:TextAttributes
g_lo_action_group_set_action_enabled - .uno:FontWork
g_lo_action_group_set_action_enabled - .uno:ObjectTitleDescription
g_lo_action_group_set_action_enabled - .uno:NameGroup
g_lo_action_group_set_action_enabled - .uno:MergeCells
g_lo_action_group_set_action_enabled - .uno:SplitCell
g_lo_action_group_set_action_enabled - .uno:Protect
g_lo_action_group_set_action_enabled - .uno:MergeTable
g_lo_action_group_set_action_enabled - .uno:SplitTable
g_lo_action_group_set_action_enabled - .uno:AutoFormat
g_lo_action_group_set_action_enabled - .uno:HeadingRowsRepeat
g_lo_action_group_set_action_enabled - .uno:TableSort
g_lo_action_group_set_action_enabled - .uno:TableNumberFormatDialog
g_lo_action_group_set_action_enabled - .uno:TableDialog
g_lo_action_group_set_action_enabled - .uno:InsertRowDialog
g_lo_action_group_set_action_enabled - .uno:InsertColumnDialog
g_lo_action_group_set_action_enabled - .uno:DeleteTable
g_lo_action_group_set_action_enabled - .uno:DeleteRows
g_lo_action_group_set_action_enabled - .uno:DeleteColumns
g_lo_action_group_set_action_enabled - .uno:SelectTable
g_lo_action_group_set_action_enabled - .uno:EntireRow
g_lo_action_group_set_action_enabled - .uno:EntireColumn
g_lo_action_group_set_action_enabled - .uno:EntireCell
g_lo_action_group_set_action_enabled - .uno:SetColumnWidth
g_lo_action_group_set_action_enabled - .uno:SetOptimalColumnWidth
g_lo_action_group_set_action_enabled - .uno:DistributeColumns
g_lo_action_group_set_action_enabled - .uno:SetRowHeight
g_lo_action_group_set_action_enabled - .uno:SetOptimalRowHeight
g_lo_action_group_set_action_enabled - .uno:DistributeRows
g_lo_action_group_set_action_enabled - .uno:RowSplit
g_lo_action_group_set_action_enabled - .uno:ConvertTextToTable
g_lo_action_group_set_action_enabled - .uno:ConvertTableToText
g_lo_action_group_set_action_enabled - .uno:SortDialog
g_lo_action_group_set_action_enabled - .uno:CalculateSel
g_lo_action_group_set_action_enabled - .uno:SetLanguageSelectionMenu
g_lo_action_group_set_action_enabled - .uno:SetLanguageParagraphMenu
g_lo_action_group_set_action_enabled - .uno:SetLanguageAllTextMenu
g_lo_action_group_set_action_enabled - .uno:HangulHanjaConversion
g_lo_action_group_set_action_enabled - .uno:HangulHanjaConversion
g_lo_action_group_set_action_enabled - .uno:ChineseConversion
g_lo_action_group_set_action_enabled - .uno:ChineseConversion
g_lo_action_group_set_action_enabled - .uno:UpdateAllLinks
g_lo_action_group_set_action_enabled - .uno:UpdateCharts
g_lo_action_group_set_action_enabled - .uno:UpdateCurIndex
g_lo_action_group_set_action_enabled - .uno:UpdateAllIndexes
g_lo_action_group_set_action_enabled - .uno:MacroRecorder
g_lo_action_group_set_action_enabled - .uno:ScriptOrganizer
g_lo_action_group_set_action_enabled - .uno:MacroSignature

```

The freeze itself, many minutes later, is not reflected in any specific message.

---

### Post by effenberg0x0 on 2012-08-27
Wise Ferret,

+1, exactly the same. I was just wondering: When Calc freezes, does your indicators continue to work? My top bar indicators stop responding to left/right click, the clock stops, etc. It does not crash, they're still there, but they're frozen.

Regards,
Effenberg

---

### Post by ftx79 on 2012-08-28
+1 for me too.

I installed Calligra 2.5 also. I don't know if it is the origin of the problem... ?

---

### Post by Wise Ferret on 2012-08-28
Effenberg, this are the same symptom I experience.
ftx, I do not have Calligra installed, so I gues that this is a pure Libre Office bug.

---

### Post by ajgreeny on 2012-08-28
> **Wise Ferret said:**
> Effenberg, this are the same symptom I experience.
ftx, I do not have Calligra installed, so I gues that this is a pure Libre Office bug.
Can I check that you areon 10.04 still as your profile says, and also which version of libreoffice are you running?

Finally how did you install it; using the ppa, or did you download the archive direct and then install using dpkg?  My version is 3.5.4.2, Build ID: 350m1(Build:2), from the ppa for ubuntu 10.04, and that behaves itself impeccably.

---

### Post by Wise Ferret on 2012-08-28
> **ajgreeny said:**
> Can I check that you areon 10.04 still as your profile says, and also which version of libreoffice are you running?


Thanks, I updated my profile. I run QQ, and Libre Office is taken directly from QQ repos. Its current version is 3.6.0.2 (360m1(Build:102)).

---

### Post by ftx79 on 2012-08-29
> **Wise Ferret said:**
> Thanks, I updated my profile. I run QQ, and Libre Office is taken directly from QQ repos. Its current version is 3.6.0.2 (360m1(Build:102)).

Yes, so do I....

And That's the same whether I use Unity from staging PPA or Unity from QQ main repository...

---

### Post by effenberg0x0 on 2012-08-29
Hi, I think I have I traced my LibreOffice crashes down to three possibilities:

- Auto-correct / spelling check features. It seems auto-correct / spell-check is triggered after some time (or some inactivity time, I'm not sure). 

- Hardware Acceleration: Disabling it in "Tools / Options / LibreOffice / View / Graphics Output" seems to make it more stable.

- Auto saving recovery info: I have disabled it by unchecking "Tools / Options / Load/Save / General / "Save AutoRecovery info every <n minutes>".
 
In both cases, it looks like you have to restart LibreOffice for the changes to have an effect. That implies killing all remaining background and zombie instances of LibreOffice (or just restarting the PC).

I'm running LibreOffice Calc for about 5 hours already with no stall/crash. 

Regards, 
Effenberg

---

### Post by Wise Ferret on 2012-08-29
> **effenberg0x0 said:**
> Auto-correct / spelling check features. It seems auto-correct / spell-check is triggered after some time (or some inactivity time, I'm not sure). 

- Hardware Acceleration: Disabling it in "Tools / Options / LibreOffice / View / Graphics Output" seems to make it more stable.

- Auto saving recovery info: I have disabled it by unchecking "Tools / Options / Load/Save / General / "Save AutoRecovery info every <n minutes>".


Unfortunately, this does not work for me. The freezes still occur regularly.

---

### Post by grahammechanical on 2012-08-30
Can I add something to this discussion. I too have notice Libreoffice sort of freezing after I left it idle for some minutes (such as watching TV). When I came back to Libreoffice it would crash when trying to save the file.

I am now using an install of Quantal based upon the 29/08/2012 ISO image. Unity is 6.2. Kernel is 3.5.0-13. Libreoffice is 3.6.0.2 Build ID: 360m1 (Build 102) and I have monitored this with top and system monitor. This is what I have found:

When Libreoffice (Writer) loads it loads soffice.bin and something called unity-panel-ser. And it is unity-panel-ser that is being naughty. It cannot be found by Synaptic so it is not a separate package. Close Libreoffice and unity-panel-ser is removed.

At load up unity-panel-ser uses 30% CPU & 3% MEM

After 1 minute it uses 99% CPU & 8% MEM

After 10 minutes it uses 99-100% CPU & 24% MEM.

On my dual core machine it soon runs one core at about 100% but it keeps taking up more memory. At some point the desktop becomes unresponsive. It is not updated and windows cannot be closed. A hard re-set is needed to shut the machine down.

Regards.

---

### Post by dino99 on 2012-08-30
on my system, unity is purged, and i get soffice.bin crunching ram and cpu with calc

---

### Post by Wise Ferret on 2012-08-30
> **grahammechanical said:**
> 
When Libreoffice (Writer) loads it loads soffice.bin and something called unity-panel-ser. And it is unity-panel-ser that is being naughty. It cannot be found by Synaptic so it is not a separate package. Close Libreoffice and unity-panel-ser is removed.


Thank you, Graham. Unfortunately, I experience freezes that have no connection to Unity. They happen in gnome-shell and gnome-classic sessions, and there is no unity-panel-ser process running.

---

### Post by effenberg0x0 on 2012-08-30
Keep in mind I'm no gdb expert. I wanted to NOP or something whatever function was outputting "g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility" apparently 1/sec, to see if I would stop seeing a huge cpu load for unity_panel_service. 

After installing debugging symbols, I ran soffice.bin in gdb and started "--calc". When I got to the endless "g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility" I Ctrl+c and printed CMD_RESTOREVISIBILITY which we know would be .cmd:RestoreVisibility because that's what we're getting in stdout (and, if you google for the source, it's static const). Just checking:
```
(gdb) p CMD_RESTOREVISIBILITY
$27 = ".cmd:RestoreVisibility"

```
Then I just threw trash in it:
```
(gdb) set variable CMD_RESTOREVISIBILITY = ""
(gdb) cont

```
So the RestoreVisibility thing is dead, openoffice is running normally, Unity panel is no longer stalled, I got no high cpu usage for unity_panel_service.  At this point you can detach, of course. 


Regards,
Effenberg

---

### Post by dino99 on 2012-09-01
And an other issue now with the latest 3.6.1~rc2-1ubuntu1 from quantal-proposed : no more menu with gnome-classic session when using calc.

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1044666](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1044666)

---

### Post by Harry33 on 2012-09-01
> **dino99 said:**
> And an other issue now with the latest 3.6.1~rc2-1ubuntu1 from quantal-proposed : no more menu with gnome-classic session when using calc.

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1044666](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1044666)

Same here, no menu at all.
I am using libreoffice-write and Gnome-shell DE.
Had to downgrade back to 3.6.0 rc 4 to solve the issue.

This same happens with the PPA version: libreoffice-quantaltest
[https://launchpad.net/~bjoern-michaelsen/+archive/libreoffice-quantaltest-20120601](https://launchpad.net/~bjoern-michaelsen/+archive/libreoffice-quantaltest-20120601)

---

### Post by dino99 on 2012-09-01
> **Harry33 said:**
> 
Had to downgrade back to 3.6.0 rc 4 to solve the issue.



no need on my system as i'm working with the stable Precise ):P

---

### Post by jerrylamos on 2012-09-01
Unity Quantal Firefox selected a large internet NY times article with a couple hundred pictures in it.  Copied and pasted into Libre Office Write.  Loaded rather slowly I didn't time it.  Bored. Selected an object (extraneous figure at the top of the page) 

Libre Office froze.  A long time later Apport processed the bug.

sudo apt-get install lxde on top of Ubuntu, selected same article copied & pasted into Libre Office Write. My impression, loaded O.K. considering a couple hundred jpg's.

Libre Office ran fine.  Saved, edited, deleted superfluous stuff.

Same Libre.  Same Ubuntu.  Same document.  Different desktop, LXDE.  

Still with LXDE Quantal Libre Write, copied a whole flock more pictures in.  Saved, exit, reload, no problem.  Ran minutes on end, maybe approaching a half hour.  BTW, Precise 2D works fine, same article.

My opinion, no way can I do that lately with Unity Quantal Libre.  

Go figure.  Added comment to launchpad bug.

---

### Post by jbicha on 2012-09-01
The disappearing menus is bad. However, the freezing LibreOffice currently in Quantal is worse so I doubt it will prevent the new LibreOffice from migrating from -proposed to Quantal. None of the non-Unity flavors ship LibreOffice and Beta 1 is next Thursday. Thanks again for reporting the bug!

---

### Post by Harry33 on 2012-09-02
What I am wondering here is why Ubuntu is using rc versions for the source of Libreoffice.
We have 3.6.0 rc4 in QQ main now and 3.6.1 rc2 in QQ-proposed.

However, the 3.6.1 has already been released:
[http://blog.documentfoundation.org/2012/08/29/the-document-foundation-announces-libreoffice-3-6-1/](http://blog.documentfoundation.org/2012/08/29/the-document-foundation-announces-libreoffice-3-6-1/)

And also, 3.6.0 was released a month ago.

---

### Post by dino99 on 2012-09-02
> **Harry33 said:**
> 

However, the 3.6.1 has already been released:
[http://blog.documentfoundation.org/2012/08/29/the-document-foundation-announces-libreoffice-3-6-1/](http://blog.documentfoundation.org/2012/08/29/the-document-foundation-announces-libreoffice-3-6-1/)



Good to know, thanks Harry, but wonder if ubuntu is tweaking it before installation ? (dependencies version ...)

---

### Post by xebian on 2012-09-02
> **dino99 said:**
> Good to know, thanks Harry, but wonder if ubuntu is tweaking it before installation ? (dependencies version ...)

Tweaking?  You mean adding bugs?  LO 3.6.1 debs from LibreOffice works perfectly.

---

### Post by jerrylamos on 2012-09-02
> **xebian said:**
> Tweaking?  You mean adding bugs?  LO 3.6.1 debs from LibreOffice works perfectly.

?  Looking at the bug report, I think it's a unity/gtk problem?  Anyway, using lxde desktop with the same libre and ubuntu, crash did not occur on a document that fails quickly with unity/compiz desktop.  1:3.6.0 Libre Office version.

Jerry

---

### Post by Harry33 on 2012-09-02
> **jerrylamos said:**
> ?  Looking at the bug report, I think it's a unity/gtk problem?  Anyway, using lxde desktop with the same libre and ubuntu, crash did not occur on a document that fails quickly with unity/compiz desktop.  1:3.6.0 Libre Office version.
Jerry

Jerry, we have here another bug, which does not concern version 3.6.0.
You see with the version 3.6.1~rc3--1ubuntu3 the menu toolbar is gone, menu cannot be found anywhere.

---

### Post by mc4man on 2012-09-02
In an ubuntu-session the menus do appear but only retain full function as long as focus never leaves the libreoffice-* window
If focus off/on then most items are greyed out

Here just remove the libreoffice-gtk package for ugly but usable in window menus in any session

---

### Post by Matt 6:27 on 2012-09-05
> **jerrylamos said:**
> ?  Looking at the bug report, I think it's a unity/gtk problem?  Anyway, using lxde desktop with the same libre and ubuntu, crash did not occur on a document that fails quickly with unity/compiz desktop.  1:3.6.0 Libre Office version.

Jerry

I'm seeing similar behavior in 12.04.1 64bit.  Freezing is rampant of late. I suspect Unity too, since it is not limited to LibreOffice in my case. 

Currently typing on my kids' Lucid-based machine. Would that it were.

---

