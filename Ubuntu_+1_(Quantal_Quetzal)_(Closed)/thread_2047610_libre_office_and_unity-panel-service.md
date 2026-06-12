---
title: "libre office and unity-panel-service"
date: 2012-08-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by handaxe on 2012-08-25
Starting yesterday I get high CPU usage by the unity-panel-service process when using Libre Office (any of the progs). No need to do anything just open it and process ramps up CPU use.  Close LO and the process returns to normal.

Invoking from CLI shows endless "g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility"

No other progs appears to do this.

i915 graphics, i386 generic kernel

Anyone else?

---

### Post by dino99 on 2012-08-25
i'm using calc daily on i386 with nouveau driver and logged as gnome-classic, and i've the same issue: after a while (> 1 hour) i get a core fully occupied (100 %) and ram eated, then complete freeze. Need to kill the process and restart calc.
As you said soffice.bin process reproduce that issue even if the user does nothing, simply open it and that trouble comes up by itself.

Might need to be reported.

---

### Post by Bowmore on 2012-08-25
Check this bug:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354)

---

### Post by handaxe on 2012-08-25
Ta Da!  Thanks Bowmore!!  I was fixated on Libre-Office and did not search far enough it seems.

> **dino99 said:**
> i'm using calc daily on i386 with nouveau driver, and i've the same issue: after a while (> 1 hour) i get a core fully occupied (100 %) and ram eated, then complete freeze. Need to kill the process and restart calc.
As you said soffice.bin process reproduce that issue even if the user does nothing, simply open it and that trouble comes up by itself.

Might need to be reported.

Just to clarify - it is the unity-panel-service process in your case as well?

If you start libreoffice from the CLI, do you get the "g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility"?

For me the trouble is apparent immediately, tho it takes a minute or so to reach 100% but I am with intel graphics.

I will add to report  if you confirm.

HA

---

### Post by dino99 on 2012-08-25
i'm logged as gnome-classic, but get the same errors into a terminal:


```
oem@dub:~$ sudo libreoffice
Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected
g_lo_action_group_set_action_enabled - .uno:AddDirect
g_lo_action_group_set_action_enabled - .uno:RecentFileList
g_lo_action_group_set_action_enabled - .uno:AutoPilotMenu
g_lo_action_group_set_action_enabled - .uno:AvailableToolbars
g_lo_action_group_set_action_enabled - .uno:ScriptOrganizer
g_lo_action_group_set_action_enabled - .uno:AddDirect
g_lo_action_group_set_action_enabled - .uno:RecentFileList
g_lo_action_group_set_action_enabled - .uno:AutoPilotMenu
g_lo_action_group_set_action_enabled - .uno:Save
g_lo_action_group_set_action_enabled - .uno:SaveAs
g_lo_action_group_set_action_enabled - .uno:SaveAll
g_lo_action_group_set_action_enabled - .uno:SendMail
g_lo_action_group_set_action_enabled - .uno:SetDocumentProperties
g_lo_action_group_set_action_enabled - .uno:Print
g_lo_action_group_set_action_enabled - .uno:PrinterSetup
g_lo_action_group_set_action_enabled - .uno:AddressBookSource
g_lo_action_group_set_action_enabled - .uno:SaveAsTemplate
g_lo_action_group_set_action_enabled - .uno:Undo
g_lo_action_group_set_action_enabled - .uno:Cut
g_lo_action_group_set_action_enabled - .uno:Copy
g_lo_action_group_set_action_enabled - .uno:Paste
g_lo_action_group_set_action_enabled - .uno:AvailableToolbars
g_lo_action_group_set_action_enabled - .uno:StatusBarVisible
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .uno:MacroRecorder
g_lo_action_group_set_action_enabled - .uno:ScriptOrganizer
g_lo_action_group_set_action_enabled - .uno:NewWindow
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .uno:AddDirect
g_lo_action_group_set_action_enabled - .uno:RecentFileList
g_lo_action_group_set_action_enabled - .uno:AutoPilotMenu
g_lo_action_group_set_action_enabled - .uno:ObjectMenue
g_lo_action_group_set_action_enabled - .uno:AvailableToolbars
g_lo_action_group_set_action_enabled - .uno:ScriptOrganizer
g_lo_action_group_set_action_enabled - .uno:AddDirect
g_lo_action_group_set_action_enabled - .uno:RecentFileList
g_lo_action_group_set_action_enabled - .uno:AutoPilotMenu
g_lo_action_group_set_action_enabled - .uno:Save
g_lo_action_group_set_action_enabled - .uno:SaveAll
g_lo_action_group_set_action_enabled - .uno:Reload
g_lo_action_group_set_action_enabled - .uno:VersionDialog
g_lo_action_group_set_action_enabled - .uno:AddressBookSource
g_lo_action_group_set_action_enabled - .uno:Undo
g_lo_action_group_set_action_enabled - .uno:Redo
g_lo_action_group_set_action_enabled - .uno:Repeat
g_lo_action_group_set_action_enabled - .uno:EditLinks
g_lo_action_group_set_action_enabled - .uno:ImageMapDialog
g_lo_action_group_set_action_enabled - .uno:ProtectTraceChangeMode
g_lo_action_group_set_action_enabled - .uno:ShowChanges
g_lo_action_group_set_action_enabled - .uno:AcceptChanges
g_lo_action_group_set_action_enabled - .uno:CommentChange
g_lo_action_group_set_action_enabled - .uno:FillDown
g_lo_action_group_set_action_enabled - .uno:FillTable
g_lo_action_group_set_action_enabled - .uno:FillSeries
g_lo_action_group_set_action_enabled - .uno:Remove
g_lo_action_group_set_action_enabled - .uno:DeleteRowbreak
g_lo_action_group_set_action_enabled - .uno:DeleteColumnbreak
g_lo_action_group_set_action_enabled - .uno:AvailableToolbars
g_lo_action_group_set_action_enabled - .uno:ViewDataSourceBrowser
g_lo_action_group_set_action_enabled - .uno:ViewDataSourceBrowser
g_lo_action_group_set_action_enabled - .uno:TaskPane
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .uno:InsertRowBreak
g_lo_action_group_set_action_enabled - .uno:InsertColumnBreak
g_lo_action_group_set_action_enabled - .uno:InsertNonBreakingSpace
g_lo_action_group_set_action_enabled - .uno:InsertHardHyphen
g_lo_action_group_set_action_enabled - .uno:InsertSoftHyphen
g_lo_action_group_set_action_enabled - .uno:InsertZWSP
g_lo_action_group_set_action_enabled - .uno:InsertZWSP
g_lo_action_group_set_action_enabled - .uno:InsertZWNBSP
g_lo_action_group_set_action_enabled - .uno:InsertZWNBSP
g_lo_action_group_set_action_enabled - .uno:InsertLRM
g_lo_action_group_set_action_enabled - .uno:InsertLRM
g_lo_action_group_set_action_enabled - .uno:InsertRLM
g_lo_action_group_set_action_enabled - .uno:InsertRLM
g_lo_action_group_set_action_enabled - .uno:FontDialog
g_lo_action_group_set_action_enabled - .uno:ParagraphDialog
g_lo_action_group_set_action_enabled - .uno:AutoFormat
g_lo_action_group_set_action_enabled - .uno:ControlProperties
g_lo_action_group_set_action_enabled - .uno:FormProperties
g_lo_action_group_set_action_enabled - .uno:Hide
g_lo_action_group_set_action_enabled - .uno:Show
g_lo_action_group_set_action_enabled - .uno:SheetRightToLeft
g_lo_action_group_set_action_enabled - .uno:ToggleMergeCells
g_lo_action_group_set_action_enabled - .uno:MergeCells
g_lo_action_group_set_action_enabled - .uno:SplitCell
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToHalfWidth
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToHalfWidth
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToFullWidth
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToFullWidth
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToHiragana
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToHiragana
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToKatakana
g_lo_action_group_set_action_enabled - .uno:ChangeCaseToKatakana
g_lo_action_group_set_action_enabled - .uno:SetAnchorToPage
g_lo_action_group_set_action_enabled - .uno:SetAnchorToCell
g_lo_action_group_set_action_enabled - .uno:BringToFront
g_lo_action_group_set_action_enabled - .uno:ObjectForwardOne
g_lo_action_group_set_action_enabled - .uno:ObjectBackOne
g_lo_action_group_set_action_enabled - .uno:SendToBack
g_lo_action_group_set_action_enabled - .uno:SetObjectToForeground
g_lo_action_group_set_action_enabled - .uno:SetObjectToBackground
g_lo_action_group_set_action_enabled - .uno:ObjectMirrorVertical
g_lo_action_group_set_action_enabled - .uno:ObjectMirrorHorizontal
g_lo_action_group_set_action_enabled - .uno:FormatGroup
g_lo_action_group_set_action_enabled - .uno:FormatUngroup
g_lo_action_group_set_action_enabled - .uno:EnterGroup
g_lo_action_group_set_action_enabled - .uno:LeaveGroup
g_lo_action_group_set_action_enabled - .uno:TransformDialog
g_lo_action_group_set_action_enabled - .uno:FormatLine
g_lo_action_group_set_action_enabled - .uno:FormatArea
g_lo_action_group_set_action_enabled - .uno:TextAttributes
g_lo_action_group_set_action_enabled - .uno:ToggleObjectBezierMode
g_lo_action_group_set_action_enabled - .uno:ScenarioManager
g_lo_action_group_set_action_enabled - .uno:HangulHanjaConversion
g_lo_action_group_set_action_enabled - .uno:HangulHanjaConversion
g_lo_action_group_set_action_enabled - .uno:ChineseConversion
g_lo_action_group_set_action_enabled - .uno:ChineseConversion
g_lo_action_group_set_action_enabled - .uno:ThesaurusDialog
g_lo_action_group_set_action_enabled - .uno:RefreshArrows
g_lo_action_group_set_action_enabled - .uno:MacroRecorder
g_lo_action_group_set_action_enabled - .uno:ScriptOrganizer
g_lo_action_group_set_action_enabled - .uno:MacroSignature
g_lo_action_group_set_action_enabled - .uno:TableOperationDialog
g_lo_action_group_set_action_enabled - .uno:TextToColumns
g_lo_action_group_set_action_enabled - .uno:DataAreaRefresh
g_lo_action_group_set_action_enabled - .uno:DataFilterRemoveFilter
g_lo_action_group_set_action_enabled - .uno:DataFilterHideAutoFilter
g_lo_action_group_set_action_enabled - .uno:ShowDetail
g_lo_action_group_set_action_enabled - .uno:Ungroup
g_lo_action_group_set_action_enabled - .uno:ClearOutline
g_lo_action_group_set_action_enabled - .uno:RecalcPivotTable
g_lo_action_group_set_action_enabled - .uno:DeletePivotTable
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
g_lo_action_group_set_action_enabled - .cmd:RestoreVisibility
```

Wonder if the font issue at the very beginning can be related to the other errors coming then.

---

### Post by mc4man on 2012-08-25
The source of all those 'g_lo_action_group ....' was from 
'unitymenu patch' which was just added

---

### Post by handaxe on 2012-08-25
Have installed lxde (lubuntu) and am testing Libre-Office in that environment.

Tnx  mac4man.  Strangely, in lxde I also get the  'g_lo_action_group ....'  errors.  However, libre-office seems to show a very slow CPU & mem  increase (will need a long test to show for sure).  In the unity-desktop  the CPU increase is immediate.  So the  'g_lo_action_group ....' stuff  if at issue yields different outcomes in different DEs.

This may be a libre-office bug that manifests differently. Reading the bug-report, including Bowmore's observation re appmenu, it is rather confusing.  I suspect there should be 2 bugs, 1 for unity another for non-unity or some such.

---

### Post by handaxe on 2012-08-25
Confirm that libre-office displays a slow climb in cpu usage as well as mem in lxde and for dino99 in a gnome-classic DE.

My guess is that some global menu stuff added to libre-office mentioned by mac4man misbehaves, with immediate effect within unity and with slower effect in non-unity DEs.

Late addition: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354/comments/7](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354/comments/7)

Thanks all.

---

### Post by handaxe on 2012-09-03
Libreoffice version 1:3.6.1~rc2-1ubuntu3 now in proposed solves issue.  It now needs lo-menubar installed to have menus under unity, or so it seems and that in turn for the moment borks LO outside of the Unity desktop.

---

### Post by dino99 on 2012-09-03
> **handaxe said:**
> Libreoffice version 1:3.6.1~rc2-1ubuntu3 now in proposed solves issue.  It now needs lo-menubar installed to have menus under unity, or so it seems and that in turn for the moment borks LO outside of the Unity desktop.

No luck on gnome-classic, most of the libreoffice upgrades want to uninstall actual packages instead of upgrading.

---

