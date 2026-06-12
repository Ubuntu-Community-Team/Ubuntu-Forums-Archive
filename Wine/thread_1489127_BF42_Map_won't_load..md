---
title: "BF42 Map won't load."
date: 2010-05-20
forum: Wine
---

### Post by River7471 on 2010-05-20
Game started through wine but the map loading icon doesn't fill.  

Any ideas?

---

### Post by cogadh on 2010-05-21
[Not without a little more info]("http://ubuntuforums.org/showthread.php?t=885111").

---

### Post by River7471 on 2010-05-21
Tosh Satellite A135 2gb ram
Ubuntu 10.....4?

Latest version of wine
Intel 945

---

### Post by cogadh on 2010-05-21
And the terminal oputput from Wine?

---

### Post by River7471 on 2010-05-21
Haven't run it using terminal, or run it while using terminal.  And I don't know how to run it from there.

---

### Post by River7471 on 2010-05-21
shawn@shawn-laptop:~$ wine Battlefield 1942
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x123ae0, filter=0x73e9d4,flags=0x00000001) returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x76e9c8): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x76e958): stub
fixme:service:EnumServicesStatusW 0x128610 type=30 state=3 (nil) 0 0x76e7e8 0x76e7f4 0x76e7f0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x76e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x123ad0,(nil)): stub
wine: cannot find L"C:\\windows\\system32\\Battlefield.exe"
shawn@shawn-laptop:~$

---

### Post by cogadh on 2010-05-21
First, you need to change directories to where the game is installed:
```
cd ~/.wine/drive_c/Program\ Files/<BF1942 install directory>
```
Obviously, replace that <BF1942 install directory> with the correct info.

Once you have changed directories, then you need to "wine" the executable:
```
wine <BF1942>.exe
```
Again, replace that <BF1942> with the correct file name. Now you should get the correct terminal output.

---

### Post by River7471 on 2010-05-21
Is there a terminal command to list the location of the bf42.exe?

Am I going to move the exe file out of the virtual c drive where the exe is now?

/home/shawn/.wine/dosdevices/c:/Program Files/EA GAMES/Battlefield 1942

Thanks for the help.

---

### Post by River7471 on 2010-05-21
shawn@shawn-laptop:~$ cd ~/.wine/drive_c/Program\ Files/<BF1942 install directory>
bash: syntax error near unexpected token `newline'
shawn@shawn-laptop:~$ cd ~/.wine/drive_c/Program Files/EA GAMES/Battlefield 1942bash: cd: /home/shawn/.wine/drive_c/Program: No such file or directory
shawn@shawn-laptop:~$ cd: /home/shawn/.wine/drive_c/Program: No such file or directory
No command 'cd:' found, did you mean:
 Command 'cda' from package 'xmcd' (universe)
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdw' from package 'cdw' (universe)
 Command 'cd5' from package 'cd5' (universe)
 Command 'cdp' from package 'irpas' (multiverse)
cd:: command not found
shawn@shawn-laptop:~$ cd /home/shawn/.wine/drive_c/Program: No such file or directory
bash: cd: /home/shawn/.wine/drive_c/Program:: No such file or directory
shawn@shawn-laptop:~$ cd home/shawn/.wine/drive_c/Program: No such file or directory
bash: cd: home/shawn/.wine/drive_c/Program:: No such file or directory
shawn@shawn-laptop:~$

---

### Post by cogadh on 2010-05-21
Okay, assuming that is the correct install path, you need to modify that "cd" command a bit:
```
cd ~/.wine/drive_c/Program\ Files/EA\ GAMES/Battlefield\ 1942
```
You have to add a "\" before any spaces in a file or directory name in order for Linux to recognize that there is a space there.

---

### Post by River7471 on 2010-05-21
hawn@shawn-laptop:~$ cd ~/.wine/drive_c/Program\ Files/EA\ GAMES/Battlefield\ 1942
[email]shawn@shawn-laptop:~/.wine[/email]/drive_c/Program Files/EA GAMES/Battlefield 1942$ wine <BF1942>.exe
bash: BF1942: No such file or directory
[email]shawn@shawn-laptop:~/.wine[/email]/drive_c/Program Files/EA GAMES/Battlefield 1942$ wine <BF1942>.exe
bash: BF1942: No such file or directory
[email]shawn@shawn-laptop:~/.wine[/email]/drive_c/Program Files/EA GAMES/Battlefield 1942$ 
[email]shawn@shawn-laptop:~/.wine[/email]/drive_c/Program Files/EA GAMES/Battlefield 1942$ wine Battlefield 1942.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x123ae0, filter=0x73e9d4,flags=0x00000001) returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x76e9c8): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x76e958): stub
fixme:service:EnumServicesStatusW 0x128610 type=30 state=3 (nil) 0 0x76e7e8 0x76e7f4 0x76e7f0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x76e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x123ad0,(nil)): stub
wine: cannot find L"C:\\windows\\system32\\Battlefield.exe"
[email]shawn@shawn-laptop:~/.wine[/email]/drive_c/Program Files/EA GAMES/Battlefield 1942$

---

### Post by asdfoo on 2010-05-21
type 'ls' to see the files in a directory


for reference, the main executable of this game is bf1942.exe

you need to install the patches before playing the game online though links here

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7591](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7591)

---

### Post by River7471 on 2010-05-21
Maybe that is it.  I installed the larger patch, and not the smaller one, thinking that it included the smaller patch.

I also wasn't sure if installing both patches which got installed first, or if the order mattered.

---

### Post by River7471 on 2010-05-21
I found the order for the patches.  Larger one first, then the smaller patch.  Now the game won't even run the BF trailer.  Screen goes black and locks up.

The info at the end of the terminal process looks like it might mean something to someone who knows more than a Ubuntu beginner like me.  "Can't choose pixel format..."




.......................
found key:TOOLTIP_KETTENKRAD_HEADING
found key:TOOLTIP_KETTENKRAD
found key:OBJECTIVEMODE
found key:VICTORY
found key:DEFEAT
found key:Factory
found key:AXIS_DESTROYED_OBJECTIVE1
found key:ALLIES_DESTROYED_OBJECTIVE1
found key:CREDITS_FREE_CONTENT
found key:CREDITS_1_6_FORWARD
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:service:EnumServicesStatusW 0x128818 type=30 state=3 (nil) 0 0x76e7d0 0x76e7dc 0x76e7d8
Killed

---

### Post by River7471 on 2010-05-21
Screenshot links for my wine configs

[[IMG]http://img138.imageshack.us/img138/4964/screenshot1zr.th.png[/IMG]](http://img138.imageshack.us/i/screenshot1zr.png/)

[http://img138.imageshack.us/i/screenshot1zr.png/](http://img138.imageshack.us/i/screenshot1zr.png/)

[IMG]http://img195.imageshack.us/img195/3024/screenshot2vi.png[/IMG]

[IMG]http://img715.imageshack.us/img715/7506/screenshot3gu.png[/IMG]

---

### Post by River7471 on 2010-05-22
found key:Kharkov_Hills
found key:SOUND_OPTIONS_HARDWARE
found key:DEBRIEFING_DRAW
found key:INFO_MESSAGE_PLEASE_WAIT
found key:ERROR_BANNED_FROM_SERVER
found key:Joystick_IDButton_16
found key:Joystick_IDButton_17
found key:Joystick_IDButton_18
found key:Joystick_IDButton_19
found key:Joystick_IDButton_20
found key:Joystick_IDButton_21
found key:Joystick_IDButton_22
found key:Joystick_IDButton_23
found key:Joystick_IDButton_24
found key:Joystick_IDButton_25
found key:Joystick_IDButton_26
found key:Joystick_IDButton_27
found key:Joystick_IDButton_28
found key:Joystick_IDButton_29
found key:Joystick_IDButton_30
found key:Joystick_IDButton_31
found key:Demo Wake
found key:Demo_Wake
found key:IDKey_OEM_102
found key:controlpoint_allies_right
found key:controlpoint_allies_middle
found key:controlpoint_allies_left
found key:controlpoint_axis_right
found key:controlpoint_axis_middle
found key:controlpoint_axis_left
found key:cammobunker
found key:bridgebunker
found key:Allied_Bunker_Cpoint
found key:Axis_Bunker_Cpoint
found key:broaxis_Cpoint 
found key:midbase_suribashibottom
found key:OpenSpawnPoint_alliedside_stnbrdgbunker
found key:The_Radar_Bunker
found key:South_Midway
found key:North_Midway
found key:CONTROLPOINT_stalingrad
found key:openbasecammo 
found key:NEW KEYS 02/10/09 PATCH 1.2 NEW_KEYS_NEW_KEYS_NEW_KEYS
found key:MULTIPLAYER_CUSTOM_GAME_FILTER_HEADING
found key:MENU_CUSTOM_GAME
found key:MULTIPLATER_APPLY_FILTER
found key:MULTIPLATER_APPLY
found key:CUSTOM_GAME_ACTIVATE
found key:CUSTOM_GAME_VISIT_WEB_PAGE
found key:CUSTOM_GAME_DESCRIPTION
found key:CUSTOM_GAME_VERSION
found key:MULTIPLAYER_INFO
found key:FILTER_ALL
found key:MULTIPLATER_CLEAR_FILTER
found key:MENU_STOP
found key:XPack1
found key:FILTER_NOT_PASSWORD
found key:FILTER_FAVORITES
found key:FILTER_FAVORITES_ADD
found key:FILTER_FAVORITES_REMOVE
found key:FILTER_NOT_FULL
found key:FILTER_NOT_EMPTY
found key:FILTER_DEDICATED_ONLY
found key:CUSTOM_GAME_NAME
found key:CUSTOM_GAME_INFO
found key:XPACK1_INFO
found key:INSERT_CD_XPACK1
found key:ERROR_UNKNOWN
found key:INFO_MESSAGE_MAP_NOT_FOUND
found key:ERROR_MESSAGE_FILE_NOT_FOUND
found key:ERROR_MESSAGE_CORRUPT_DATA
found key:ERROR_MESSAGE_FILE_DIFFERS
found key:ERROR_MESSAGE_DATA_DIFFERS
found key:ERROR_BANNED_FROM_SERVER
found key:INFO_MESSAGE_SERVER_SHUTTING_DOWN
found key:INFO_MESSAGE_DOWNLOAD_QUESTION
found key:INFO_MESSAGE_MAP_NOT_FOUND_DOWNLOAD_QUESTION
found key:NEW KEYS 02/10/09 PATCH 1.3 NEW_KEYS_NEW_KEYS_NEW_KEYS
found key:MULTIPLAYER_BRIEFING_CORRAL_SEA
found key:DEBRIEFING_ALLIED_MAJOR_VICTORY+A1393_CORRAL_SEA
found key:DEBRIEFING_ALLIED_MINOR_VICTORY_CORRAL_SEA
found key:DEBRIEFING_ALLIED_MAJOR_DEFEAT_CORRAL_SEA
found key:DEBRIEFING_ALLIED_MINOR_DEFEAT_CORRAL_SEA
found key:DEBRIEFING_AXIS_MAJOR_VICTORY_CORRAL_SEA
found key:DEBRIEFING_AXIS_MINOR_VICTORY_CORRAL_SEA
found key:DEBRIEFING_AXIS_MAJOR_DEFEAT_CORRAL_SEA
found key:DEBRIEFING_AXIS_MINOR_DEFEAT_CORRAL_SEA
found key:CREDITS_GAME_DESIGN
found key:CREDITS_LANGUAGE_TESTING_MANAGER
found key:CREDITS_LANGUAGE_PROJECT_LEAD_MANAGER
found key:CREDITS_LANGUAGE_MANAGER_TESTING
found key:Coral_Sea
found key:Coral Sea
found key:CREDITS_GAMESPY_LEGAL
found key:CREDITS
found key:Hiryu
found key:Hornet
found key:MULTIPLAYER_BRIEFING_ABERDEEN
found key:ABERDEEN
found key:west_outpost
found key:NEW KEYS 1.4
found key:RESERVED_PASSWORD_INVALID
found key:MENU_RESERVED_PASSWORD
found key:RESERVED_PASSWORD
found key:RESERVED_SLOTS
found key:BATTLE OF BRITAIN KEYS
found key:BATTLE_OF_BRITAIN
found key:BATTLE OF BRITAIN
found key:West_Harwick_RadarTower
found key:East_Harwick_RadarTower
found key:Clacton_RadarTower
found key:Felixstowe_RadarTower
found key:JU88A
found key:MULTIPLAYER_BRIEFING_BRITAIN
found key:DEBRIEFING_ALLIED_MAJOR_VICTORY_BRITAIN
found key:DEBRIEFING_ALLIED_MINOR_VICTORY_BRITAIN
found key:DEBRIEFING_ALLIED_MAJOR_DEFEAT_BRITAIN
found key:DEBRIEFING_ALLIED_MINOR_DEFEAT_BRITAIN
found key:DEBRIEFING_AXIS_MAJOR_VICTORY_BRITAIN
found key:DEBRIEFING_AXIS_MINOR_VICTORY_BRITAIN
found key:DEBRIEFING_AXIS_MAJOR_DEFEAT_BRITAIN
found key:DEBRIEFING_AXIS_MINOR_DEFEAT_BRITAIN
found key:NEW KEYS 1.45
found key:TOOLTIP_DEFGUN_HEADING
found key:TOOLTIP_DEFGUN
found key:CREDITS_EXECUTIVE_PRODUCER
found key:CREDITS_PRODUCER_SWEDEN
found key:CREDITS_PRODUCER_SWEDEN_LOC
found key:CREDITS_PRODUCER_CANADA
found key:CREDITS_LEVEL_DESIGN
found key:CREDITS_LEAD_ART_ART_DIRECTOR
found key:CREDITS_ART_TECHNICAL_DIRECTOR
found key:CREDITS_LEVEL_ART
found key:CREDITS_SPECIAL_EFFECTS
found key:CREDITS_ADDITIONAL_DESIGN
found key:CREDITS_ADDITIONAL_ART
found key:CREDITS_ADDITIONAL_SOUND
found key:CREDITS_ASSISTANT_PRODUCER
found key:CREDITS_LOCALIZATION_COORDINATOR
found key:CREDITS_QA_MANAGER
found key:CREDITS_QA_PROJECT_MANAGERS
found key:CREDITS_QA_PROJECT_LEADER
found key:CREDITS_QA_TEAM_LEADERS
found key:CREDITS_QUALITY_ASSURANCE_TEAM
found key:CREDITS_TECH_COMPLIANCE_MAN
found key:CREDITS_TECH_SUPERVISOR
found key:CREDITS_TECH_REQUIREMENTS_AUDIT
found key:CREDITS_QA_TECHS
found key:CREDITS_EUROPEAN_MASTERING_MAN
found key:CREDITS_MASTERING_COORDINATOR
found key:CREDITS_MASTERING_TECHNICIANS
found key:CREDITS_NETWORK_SYSADMIN
found key:CREDITS_CQC_EUR
found key:CREDITS_CQC_US
found key:CREDITS_CQC_EUR_OPS_MAN
found key:CREDITS_CQC_EUR_TEST_MAN
found key:CREDITS_CQC_EUR_TEST_SUP
found key:CREDITS_CQC_EUR_TEST_LEADS
found key:CREDITS_CQC_EUR_TEST_SEN
found key:CREDITS_CQC_EUR_PLAT_MAN
found key:CREDITS_CQC_EUR_PLAT_SPEC
found key:CREDITS_ITAL_LOC_MAN
found key:CREDITS_ITAL_TRANS_SUP
found key:CREDITS_ITAL_LT_SUP
found key:CREDITS_SPAN_LOC
found key:CREDITS_SPAN_LOC_COORD
found key:CREDITS_TRANS
found key:CREDITS_TESTER
found key:CREDTS_DOC
found key:CREDITS_EA_GERMANY
found key:CREDITS_LOC_MAN
found key:CREDITS_GERM_LOC_COORD
found key:CREDITS_LEAD_TEST
found key:CREDITS_LANG_TEST
found key:CREDITS_EA_FRANCE
found key:CREDITS_PRODUCT_MAN
found key:CREDITS_LOC_MAN
found key:CREDITS_TRANS_MAN
found key:CREDITS_TRANS_COORD
found key:CREDITS_TRANSLATION
found key:CREDITS_TEST_MAN
found key:CREDITS_TEST_COORD
found key:CREDITS_MASTERING_US
found key:CREDITS_LOC_PROJ_MAN
found key:CREDITS_PROD_SERV
found key:CREDITS_PROD_MANAGER
found key:CREDITS_ACCT_EXEC
found key:CREDITS_DOC_LAYOUT_COORD
found key:CREDITS_PROD_PLAN
found key:CREDITS_CREAT_SERV
found key:CREDITS_PROJECT_MAN
found key:CREDITS_QA_LT
found key:CREDITS_QA_LT_PROJ_LEAD
found key:CREDITS_QA_LT_TEAM_LEAD
found key:CREDITS_QA_LT_TEAM
found key:CREDITS_DTP_SUP
found key:CREDITS_DTP_ASST
found key:CREDITS_LT_SUP
found key:CREDITS_ITAL_TESTERS
found key:CREDITS_SOPS
found key:CREDITS_QA
found key:CREDITS_TECH_COMPLIANCE_GR
found key:CREDITS_MASTERING
found key:CREDITS_EA_ITALY
found key:CREDITS_ITAL_LOC_COORD
found key:XPACK2 KEYS
found key:XPACK2_INFO
found key:XPack2
found key:INSERT_CD_XPACK2
found key:CREATE_GAME_ATICK
found key:NEW KEYS PATCH 1.5
found key:INVASION_OF_THE_PHILIPPINES
found key:INVASION OF THE PHILIPPINES
found key:East_Harbor
found key:West_Harbor
found key:US_Marine_Base
found key:Point_Boyington
found key:Airfield
found key:Islands
found key:Type38
found key:Elco80
found key:BlackMedal
found key:Ho-Ha
found key:M1Garand
found key:Type5
found key:TOOLTIP_PTBOAT_HEADING
found key:TOOLTIP_PTBOAT
found key:TOOLTIP_PTRAFT_HEADING
found key:TOOLTIP_PTRAFT
found key:NEW KEYS PATCH 1.6
found key:CHAT_FLOOD_ERROR
found key:SCOREBOARD_ADD_BUDDY
found key:SCOREBOARD_DROP_BUDDY
found key:SCOREBOARD_VOTE_KICK
found key:SCOREBOARD_VOTE_KICK_TEAM
found key:SCOREBOARD_BRINGUP_MAPVOTE
found key:SCOREBOARD_LOCK
found key:SCOREBOARD_VOTE_MAP
found key:RESPAWN_SCOREBOARD
found key:MAPVOTE_HEADING
found key:VOTEMSG_MAP_PROGRESS
found key:VOTEMSG_MAP_NONCONCLUSIVE
found key:VOTEMSG_MAP_SUCCESS
found key:VOTEMSG_MAP_INACTIVE
found key:VOTEMSG_TEAMKICK_PROGRESS
found key:VOTEMSG_TEAMKICK_NONCONCLUSIVE
found key:VOTEMSG_TEAMKICK_SUCCESS
found key:VOTEMSG_KICK_PROGRESS
found key:VOTEMSG_KICK_SUCCESS
found key:VOTEMSG_KICK_NONCONCLUSIVE
found key:VOTEMSG_KICK_INACTIVE
found key:VOTEFEEDBACK_MAP
found key:VOTEFEEDBACK_KICK
found key:VOTEFEEDBACK_TEAMKICK
found key:VOTE_CAST
found key:VOTE_TIME_LEFT
found key:VOTE_YES
found key:VOTE_NO
found key:VOTE_NEEDED
found key:FILTER_PURE_ONLY
found key:FILTER_NONEMPTY_ONLY
found key:FILTER_FAVORITES_ONLY
found key:FILTER_OFFICIAL_STATS_ONLY
found key:ADD_FAVORITE
found key:REMOVE_FAVORITE
found key:MAPVOTE_MAPNAME
found key:MAPVOTE_ID
found key:MAPVOTE_MOD
found key:MAPVOTE_GAMEMODE
found key:MAPVOTE_NUMVOTES
found key:CREDITS_PATCH_PROGRAMMING
found key:CREDITS_1_31_FORWARD
found key:LEGEND_TITLE
found key:LEGEND_MODS
found key:LEGEND_RTR
found key:LEGEND_SW
found key:LEGEND_UNKNOWN_MOD
found key:LEGEND_MIXED_MOD
found key:LEGEND_CUSTOM_ICONS
found key:LEGEND_OTHER
found key:LEGEND_PASSWORD
found key:LEGEND_PURE
found key:LEGEND_OFFICIAL_STATS
found key:LEGEND_SERVER_SPEC
found key:LEGEND_WIN
found key:LEGEND_DED
found key:LEGEND_LINUX
found key:LEGEND_CPU_LOAD
found key:LEGEND_HIGH
found key:LEGEND_MEDIUM
found key:LEGEND_LOW
found key:LIBERATION_OF_CAEN
found key:LIBERATION OF CAEN
found key:Canadian_Base
found key:South_River
found key:Pegasus_Bridge
found key:Church
found key:Park
found key:German_Headquarters
found key:Lynx
found key:Sexton
found key:Kettenkrad
found key:JohnsonLMG
found key:Ilyushin
found key:MULTIPLAYER_BRIEFING_CAEN
found key:AXIS_OBJECTIVE_TIMER_TIMED_OUT1
found key:ALLIES_OBJECTIVE_TIMER_TIMED_OUT1
found key:ALLIES_OBJECTIVE_ACCOMPLISHED1
found key:AXIS_OBJECTIVE_ACCOMPLISHED1
found key:RENT_SERVER
found key:CONTROLS_COMMON_SHOWMAPVOTE
found key:CONTROLS_COMMON_VOTEYES
found key:CONTROLS_COMMON_VOTENO
found key:PB_ENABLE
found key:FILTER_PB_ONLY
found key:PB_JOIN_ERROR
found key:PB_ENABLE_ERROR
found key:PB_DISABLE
found key:PB_DISABLE_NEXT
found key:PB_ENABLE_REQUIRE
found key:LEGEND_PB
found key:CREDITS_FREE_CONTENT
found key:CREDITS_1_6_FORWARD
found key:AXIS_DESTROYED_OBJECTIVE1
found key:ALLIES_DESTROYED_OBJECTIVE1
found key:OBJECTIVEMODE
found key:TOOLTIP_COMMANDORAFT_HEADING
found key:TOOLTIP_COMMANDORAFT
found key:TOOLTIP_ANTI_TANK_GUN_HEADING
found key:TOOLTIP_ANTI_TANK_GUN
found key:TOOLTIP_KETTENKRAD_HEADING
found key:TOOLTIP_KETTENKRAD
found key:OBJECTIVEMODE
found key:VICTORY
found key:DEFEAT
found key:Factory
found key:AXIS_DESTROYED_OBJECTIVE1
found key:ALLIES_DESTROYED_OBJECTIVE1
found key:CREDITS_FREE_CONTENT
found key:CREDITS_1_6_FORWARD
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:service:EnumServicesStatusW 0x128818 type=30 state=3 (nil) 0 0x76e7d0 0x76e7dc 0x76e7d8
Unhandled exception: page fault on read access to 0x0000000f in 32-bit code (0x6823a137).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6823a137 ESP:0033f440 EBP:0033f7a8 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:68285ff4 ECX:b0b7b03b EDX:00000000
 ESI:00000000 EDI:01001868
Stack dump:
0x0033f440:  00000150 00410033 0033f4ac 7bc4613e
0x0033f450:  002d0036 00320032 00320032 00000080
0x0033f460:  00110000 7bc99ff4 7bc46e71 09818000
0x0033f470:  00000002 01052b98 00320032 7bc99ff4
0x0033f480:  01018000 01018028 0033f4d8 7bc472d7
0x0033f490:  ffffffff 0033f4bc 0033f4b8 00008000
Backtrace:
=>0 0x6823a137 NdrDllRegisterProxy+0x27() in rpcrt4 (0x0033f7a8)
  1 0x3580a20f in msvidctl (+0xa20e) (0x0033f7e0)
  2 0x010046bc in dxdllreg (+0x46bb) (0x0033fb50)
  3 0x01004b09 in dxdllreg (+0x4b08) (0x0033fd80)
  4 0x01005b04 in dxdllreg (+0x5b03) (0x0033fea8)
  5 0x7b858534 in kernel32 (+0x48533) (0x0033fee8)
  6 0x7bc6f584 call_thread_func+0xb() in ntdll (0x0033fef8)
  7 0x7bc6f750 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  8 0x7bc4b0aa in ntdll (+0x3b0a9) (0x0033ffe8)
0x6823a137 NdrDllRegisterProxy+0x27 in rpcrt4: movzbl	0xf(%esi),%eax
Modules:
Module	Address			Debug info	Name (88 modules)
PE	  470000-  493000	Deferred        devenum
PE	 1000000- 1018000	Export          dxdllreg
ELF	20000000-20087000	Deferred        winmm<elf>
  \-PE	20010000-20087000	\               winmm
ELF	2210a000-2213d000	Deferred        uxtheme<elf>
  \-PE	22110000-2213d000	\               uxtheme
ELF	2731c000-27364000	Deferred        dsound<elf>
  \-PE	27320000-27364000	\               dsound
ELF	2c3c6000-2c4ac000	Deferred        oleaut32<elf>
  \-PE	2c3e0000-2c4ac000	\               oleaut32
PE	35500000-35708000	Deferred        quartz
PE	35800000-35879000	Export          msvidctl
ELF	60964000-60a32000	Deferred        comctl32<elf>
  \-PE	60970000-60a32000	\               comctl32
ELF	68000000-6801d000	Deferred        ld-linux.so.2
ELF	6801d000-68158000	Export          libwine.so.1
ELF	68158000-68171000	Deferred        libpthread.so.0
ELF	68171000-68197000	Deferred        libm.so.6
ELF	68197000-6819f000	Deferred        libnss_compat.so.2
ELF	6819f000-681b6000	Deferred        libnsl.so.1
ELF	681b6000-681c2000	Deferred        libnss_files.so.2
ELF	681c2000-6821b000	Deferred        advapi32<elf>
  \-PE	681d0000-6821b000	\               advapi32
ELF	6821b000-6828c000	Export          rpcrt4<elf>
  \-PE	68230000-6828c000	\               rpcrt4
ELF	6828c000-682e5000	Deferred        setupapi<elf>
  \-PE	682a0000-682e5000	\               setupapi
ELF	682e5000-6831b000	Deferred        winspool<elf>
  \-PE	682f0000-6831b000	\               winspool
ELF	6831b000-6842a000	Deferred        user32<elf>
  \-PE	68330000-6842a000	\               user32
ELF	6842a000-684b4000	Deferred        gdi32<elf>
  \-PE	68440000-684b4000	\               gdi32
ELF	684b4000-684cd000	Deferred        version<elf>
  \-PE	684c0000-684cd000	\               version
ELF	684cd000-684e1000	Deferred        lz32<elf>
  \-PE	684d0000-684e1000	\               lz32
ELF	684e1000-68557000	Deferred        libfreetype.so.6
ELF	68557000-6856c000	Deferred        libz.so.1
ELF	6856c000-6859c000	Deferred        libfontconfig.so.1
ELF	6859c000-685c3000	Deferred        libexpat.so.1
ELF	685c3000-68662000	Deferred        winex11<elf>
  \-PE	685d0000-68662000	\               winex11
ELF	68662000-6866b000	Deferred        libsm.so.6
ELF	6866b000-68684000	Deferred        libice.so.6
ELF	68684000-68694000	Deferred        libxext.so.6
ELF	68694000-68699000	Deferred        libuuid.so.1
ELF	68699000-686b3000	Deferred        libxcb.so.1
ELF	686b3000-686b9000	Deferred        libxdmcp.so.6
ELF	686b9000-686bd000	Deferred        libxinerama.so.1
ELF	686bd000-686c3000	Deferred        libxxf86vm.so.1
ELF	686c3000-686cd000	Deferred        libxrender.so.1
ELF	686cd000-686d5000	Deferred        libxrandr.so.2
ELF	686d5000-686db000	Deferred        libxfixes.so.3
ELF	686db000-686e5000	Deferred        libxcursor.so.1
ELF	686e5000-6872b000	Deferred        libcups.so.2
ELF	6872b000-6875a000	Deferred        libgssapi_krb5.so.2
ELF	6875a000-687f5000	Deferred        libgnutls.so.26
ELF	687f5000-68806000	Deferred        libavahi-client.so.3
ELF	68806000-688b7000	Deferred        libkrb5.so.3
ELF	688b7000-688db000	Deferred        libk5crypto.so.3
ELF	688db000-688df000	Deferred        libcom_err.so.2
ELF	688df000-688e7000	Deferred        libkrb5support.so.0
ELF	688e7000-688eb000	Deferred        libkeyutils.so.1
ELF	688eb000-688ff000	Deferred        libresolv.so.2
ELF	688ff000-68910000	Deferred        libtasn1.so.3
ELF	68910000-68949000	Deferred        libdbus-1.so.3
ELF	68949000-68952000	Deferred        librt.so.1
ELF	68952000-68957000	Deferred        libgpg-error.so.0
ELF	6a7e6000-6a7ea000	Deferred        libxcomposite.so.1
ELF	6b9e3000-6bb00000	Deferred        libx11.so.6
ELF	6c9c8000-6cac4000	Deferred        ole32<elf>
  \-PE	6c9e0000-6cac4000	\               ole32
ELF	7355f000-736b9000	Deferred        libc.so.6
ELF	73a9a000-73abb000	Deferred        imm32<elf>
  \-PE	73aa0000-73abb000	\               imm32
ELF	74c57000-74cca000	Deferred        libgcrypt.so.11
ELF	75117000-75123000	Deferred        libavahi-common.so.3
ELF	78874000-788e4000	Deferred        msvcrt<elf>
  \-PE	78890000-788e4000	\               msvcrt
ELF	78f54000-78f58000	Deferred        libdl.so.2
ELF	7a125000-7a12f000	Deferred        libnss_nis.so.2
ELF	7b800000-7b93a000	Export          kernel32<elf>
  \-PE	7b810000-7b93a000	\               kernel32
ELF	7bc00000-7bcb6000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb6000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d10f000-7d113000	Deferred        libxau.so.6
Threads:
process  tid      prio (all id:s are in hex)
00000008 bf1942.exe
	00000040   15
	0000003f    1
	0000003e   15
	0000003c    0
	00000009    0
0000000e services.exe
	00000042    0
	00000041    0
	00000031    0
	0000002b    0
	00000024    0
	0000001d    0
	00000010    0
	0000000f    0
0000001a mDNSResponder.exe
	00000022    0
	00000021    0
	0000001e    0
	0000001c    0
	0000001b    0
0000001f dxdllreg.exe
	00000025    0
	00000023    0
	00000020    0
00000026 winedevice.exe
	0000002d    0
	0000002c    0
	0000002a    0
	00000027    0
00000028 (D) C:\windows\system32\dxdllreg.exe
	00000029    0 <==
0000002e winedevice.exe
	00000032    0
	00000030    0
	0000002f    0
00000037 explorer.exe
	00000038    0
Backtrace:
=>0 0x6823a137 NdrDllRegisterProxy+0x27() in rpcrt4 (0x0033f7a8)
  1 0x3580a20f in msvidctl (+0xa20e) (0x0033f7e0)
  2 0x010046bc in dxdllreg (+0x46bb) (0x0033fb50)
  3 0x01004b09 in dxdllreg (+0x4b08) (0x0033fd80)
  4 0x01005b04 in dxdllreg (+0x5b03) (0x0033fea8)
  5 0x7b858534 in kernel32 (+0x48533) (0x0033fee8)
  6 0x7bc6f584 call_thread_func+0xb() in ntdll (0x0033fef8)
  7 0x7bc6f750 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  8 0x7bc4b0aa in ntdll (+0x3b0a9) (0x0033ffe8)
Killed
[email]shawn@shawn-laptop:~/.wine[/email]/drive_c/Program Files/EA GAMES/Battlefield 1942$

---

### Post by asdfoo on 2010-05-23
Please address each of these points.

1. have you installed any non-standard software like strange dlls or what not?  If yes, you'll need to start again fresh without doing this.  The way to do this is to move your old wine prefix (all your wine data, programs you installed with wine) somewhere else if you want to keep the data - OR - delete it

to move:  mv ~/.wine ~/.wine-old
to delete: rm -rf ~/.wine

2.  If you have not installed anything else except for 1942 and the patches I linked:

a) which Wine version are you using? wine-1.2rc1 is the most recent, followed by 1.1.44.  If neither of those, please upgrade.

b) which video card and drivers do you have?

The following command will tell you near the top of the output, also make sure it says Direct Rendering: yes

glxinfo 


Finally, If you have a nvidia video card, ensure you are using the most recent driver version.  For Nvidia 6xxx series cards and newer, this will be something like 195.xx.xx or 196.xx.xx.

---

### Post by River7471 on 2010-05-23
Rendering yes.

Most recent Wine.

Video:twisted:

I'm hoping for a miracle probably.  Intel 945.  Probably a complete waste of your time.  

Toshiba Sat A135.  I don't even think it is upgradeable in the video card area.

I installed Direct X after this thread got going, thinking that might cure it then read that Wine isn't compat with Dx.  So, I uninstalled Wine, and reinstalled BF42, and am going to installed the patches again, and see what happens.

I heard of Cedega today, and saw they don't support Intel 945 so this is probably a waste of time for you.  Unless you can tell me if it is possible to upgrade the graphics without changing computers.  

Thanks anyway.

---

### Post by asdfoo on 2010-05-23
> **River7471 said:**
> Rendering yes.

Most recent Wine.

Video:twisted:

I'm hoping for a miracle probably.  Intel 945.  Probably a complete waste of your time.  

Toshiba Sat A135.  I don't even think it is upgradeable in the video card area.

I installed Direct X after this thread got going, thinking that might cure it then read that Wine isn't compat with Dx.  So, I uninstalled Wine, and reinstalled BF42, and am going to installed the patches again, and see what happens.

I heard of Cedega today, and saw they don't support Intel 945 so this is probably a waste of time for you.  Unless you can tell me if it is possible to upgrade the graphics without changing computers.  

Thanks anyway.

Intel cards don't have very good driver support on linux (lack of support from Intel) which may be the problem you're encountering.   I've tested BF1942 regularly for the past 1.5 years and it's worked pretty much flawlessly (except for punkbuster, that is designed only to work with genuine windows) with my nvidia geforce 8800 (desktop).

Since this is a laptop I don't think it's going to be possible to upgrade the video card.

This isn't to say that it's impossible to get BF 1942 working, just perhaps no one has done it yet or it may require some fixes in Wine.

I guess the most realistic option would be to play the game on Windows.

---

