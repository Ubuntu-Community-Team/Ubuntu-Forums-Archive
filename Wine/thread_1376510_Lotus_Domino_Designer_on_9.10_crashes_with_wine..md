---
title: "Lotus Domino Designer on 9.10 crashes with wine."
date: 2010-01-09
forum: Wine
---

### Post by felixdzerzhinsky on 2010-01-09
I am trying to install Domino Designer 8.5.1 with wine on Ubuntu 9.10. I am getting the following error:


```
felixdz@gUn:~/Downloads/Lotus$ wine C1SD8EN.exe 
fixme:advapi:LookupAccountNameW (null) L"felixdz" (nil) 0x33f864 (nil) 0x33f868 0x33f85c - stub
fixme:advapi:LookupAccountNameW (null) L"felixdz" 0x144be0 0x33f864 0x144ef8 0x33f868 0x33f85c - stub
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
# ***************************************************************** 
#                                                                   
# Licensed Materials - Property of IBM                              
#                                                                   
# L-GHUS-76ALYE                                                     
#                                                                   
# Copyright IBM Corp. 2003, 2008  All Rights Reserved.              
#                                                                   
# US Government Users Restricted Rights - Use, duplication or       
# disclosure restricted by GSA ADP Schedule Contract with           
# IBM Corp.                                                         
#                                                                   
# ***************************************************************** 

# NLS_ENCODING=UNICODE
# NLS_MARKUP=IBMJDK21

## G11N GA UI
# NLS_MESSAGEFORMAT_ALL 

Activities.name = Activities
Activities.description= Activities makes it easy to track your work with a dashboard, and created shared tasks.
CAE.name=Composite Application Editor
CAE.description= Composite Application Editor feature. Select this feature to install Composite Application Editor.
Editors.name=IBM Lotus Symphony 
Editors.description= The IBM Lotus Symphony contains a word processor, spreadsheet, and presentation tool. They read Microsoft Office file formats.
Feedreader.name=Feed Reader
Feedreader.description=Feed Reader feature. Select this feature to install Feed Reader.
Notes.Admin.Install.name=Domino Administrator
Notes.Designer.Install.name=Domino Designer
Sametime.name=Sametime (integrated)
Sametime.description= Sametime provides secure instant messaging.

fixme:msxml:DllCanUnloadNow 
err:msi:ITERATE_Actions Execution halted, action L"SetDefaultProps.5F3129E8_3AD4_4346_AEE6_A314E2DE64D9" returned 1603

```

---

