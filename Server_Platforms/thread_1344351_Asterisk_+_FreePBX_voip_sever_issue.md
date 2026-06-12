---
title: "Asterisk + FreePBX voip sever issue"
date: 2009-12-02
forum: Server Platforms
---

### Post by jimmygreen99 on 2009-12-02
I installed asterisk and FreePBX following the guidelines of this article: [http://www.powerpbx.org/Freepbx-on-ubuntu]("http://www.powerpbx.org/Freepbx-on-ubuntu") 

Now, I cannot start the asterisk server (I don't know how..) and when I run 
```
/usr/sbin/asterisk -vvvgc
```
it comes up with the following:

I would greatly appreciate any help that anybody can give me, I am not planning on using this for phoning to the outside world but rather a internal communications platform. 

```
Warning! Asterisk is not thread safe.
Asterisk SVN-branch-1.2-r231518, Copyright (C) 1999 - 2007 Digium, Inc. and others.
Created by Mark Spencer <markster@digium.com>
Asterisk comes with ABSOLUTELY NO WARRANTY; type 'show warranty' for details.
This is free software, with components licensed under the GNU General Public
License version 2 and other licenses; you are welcome to redistribute it under
certain conditions. Type 'show license' for details.
=========================================================================
Unable to open logger.conf: No such file or directory; default settings will be used.
Asterisk Event Logger Started /var/log/asterisk/event_log
Asterisk Dynamic Loader loading preload modules:
  == Manager registered action Ping
  == Manager registered action Events
  == Manager registered action Logoff
  == Manager registered action Hangup
  == Manager registered action Status
  == Manager registered action Setvar
  == Manager registered action Getvar
  == Manager registered action Redirect
  == Manager registered action Originate
  == Manager registered action Command
  == Manager registered action ExtensionState
  == Manager registered action AbsoluteTimeout
  == Manager registered action MailboxStatus
  == Manager registered action MailboxCount
  == Manager registered action ListCommands
Dec  2 18:47:31 NOTICE[16929]: manager.c:1686 init_manager: Unable to open management configuration manager.conf.  Call management disabled.
Dec  2 18:47:31 NOTICE[16929]: cdr.c:1214 do_reload: CDR simple logging enabled.
  == RTP Allocating from port range 5000 -> 31000
Asterisk PBX Core Initializing
Registering builtin applications:
 [AbsoluteTimeout]
  == Registered application 'AbsoluteTimeout'
 [Answer]
  == Registered application 'Answer'
 [BackGround]
  == Registered application 'BackGround'
 [Busy]
  == Registered application 'Busy'
 [Congestion]
  == Registered application 'Congestion'
 [DigitTimeout]
  == Registered application 'DigitTimeout'
 [Goto]
  == Registered application 'Goto'
 [GotoIf]
  == Registered application 'GotoIf'
 [GotoIfTime]
  == Registered application 'GotoIfTime'
 [ExecIfTime]
  == Registered application 'ExecIfTime'
 [Hangup]
  == Registered application 'Hangup'
 [NoOp]
  == Registered application 'NoOp'
 [Progress]
  == Registered application 'Progress'
 [ResetCDR]
  == Registered application 'ResetCDR'
 [ResponseTimeout]
  == Registered application 'ResponseTimeout'
 [Ringing]
  == Registered application 'Ringing'
 [SayNumber]
  == Registered application 'SayNumber'
 [SayDigits]
  == Registered application 'SayDigits'
 [SayAlpha]
  == Registered application 'SayAlpha'
 [SayPhonetic]
  == Registered application 'SayPhonetic'
 [SetAccount]
  == Registered application 'SetAccount'
 [SetAMAFlags]
  == Registered application 'SetAMAFlags'
 [SetGlobalVar]
  == Registered application 'SetGlobalVar'
 [SetLanguage]
  == Registered application 'SetLanguage'
 [Set]
  == Registered application 'Set'
 [SetVar]
  == Registered application 'SetVar'
 [ImportVar]
  == Registered application 'ImportVar'
 [Wait]
  == Registered application 'Wait'
 [WaitExten]
  == Registered application 'WaitExten'
  == Manager registered action DBGet
  == Manager registered action DBPut
Asterisk Dynamic Loader Starting:
 [res_agi.so] => (Asterisk Gateway Interface (AGI))
  == Registered application 'DeadAGI'
  == Registered application 'EAGI'
  == Registered application 'AGI'
 [res_musiconhold.so] => (Music On Hold Resource)
  == Registered application 'MusicOnHold'
  == Registered application 'WaitMusicOnHold'
  == Registered application 'SetMusicOnHold'
  == Registered application 'StartMusicOnHold'
  == Registered application 'StopMusicOnHold'
Dec  2 18:47:31 WARNING[16929]: res_musiconhold.c:1246 load_module: No music on hold classes configured, disabling music on hold.
 [res_config_mysql.so] => (MySQL RealTime Configuration Driver)
Dec  2 18:47:31 ERROR[16929]: res_config_mysql.c:650 mysql_reconnect: MySQL RealTime: Failed to connect database server  on  (err 2002). Check debug for more info.
Dec  2 18:47:31 WARNING[16929]: res_config_mysql.c:476 load_module: MySQL RealTime: Couldn't establish connection. Check debug.
Dec  2 18:47:31 NOTICE[16929]: config.c:868 ast_config_engine_register: Registered Config Engine mysql
MySQL RealTime driver loaded.
 [res_crypto.so] => (Cryptographic Digital Signatures)
    -- Loaded PUBLIC key 'freeworlddialup'
    -- Loaded PUBLIC key 'iaxtel'
 [res_features.so] => (Call Features Resource)
    -- Registered extension context 'parkedcalls'
    -- Added extension '700' priority 1 to parkedcalls
  == Registered application 'ParkedCall'
  == Registered application 'Park'
  == Manager registered action ParkedCalls
 [res_indications.so] => (Indications Configuration)
  == Registered application 'PlayTones'
  == Registered application 'StopPlayTones'
 [res_monitor.so] => (Call Monitoring Resource)
  == Registered application 'Monitor'
  == Registered application 'StopMonitor'
  == Registered application 'ChangeMonitor'
  == Manager registered action Monitor
  == Manager registered action StopMonitor
  == Manager registered action ChangeMonitor
 [res_adsi.so] => (ADSI Resource)
 [pbx_spool.so] => (Outgoing Spool Support)
 [pbx_dundi.so] => (Distributed Universal Number Discovery (DUNDi))
Dec  2 18:47:31 ERROR[16929]: pbx_dundi.c:4580 set_config: Unable to load config dundi.conf
  == Using TOS bits 0
  == DUNDi Ready and Listening on 0.0.0.0 port 4520
  == Registered application 'DUNDiLookup'
  == Registered custom function DUNDILOOKUP
 [pbx_config.so] => (Text Extension Configuration)
Dec  2 18:47:31 WARNING[16929]: pbx.c:3783 ast_merge_contexts_and_delete: Requested contexts didn't get merged
 [pbx_realtime.so] => (Realtime Switch)
 [pbx_ael.so] => (Asterisk Extension Language Compiler)
Dec  2 18:47:31 WARNING[16929]: pbx_ael.c:1172 ast_ael_compile: Unable to open '/etc/asterisk/extensions.ael': No such file or directory
Dec  2 18:47:31 WARNING[16929]: pbx.c:3783 ast_merge_contexts_and_delete: Requested contexts didn't get merged
 [pbx_loopback.so] => (Loopback Switch)
 [pbx_functions.so] => (Builtin dialplan functions)
  == Registered custom function MD5
  == Registered custom function CHECK_MD5
  == Registered custom function MATH
  == Registered custom function GROUP_COUNT
  == Registered custom function GROUP_MATCH_COUNT
  == Registered custom function GROUP
  == Registered custom function GROUP_LIST
  == Registered custom function FIELDQTY
  == Registered custom function REGEX
  == Registered custom function LEN
  == Registered custom function STRFTIME
  == Registered custom function EVAL
  == Registered custom function CDR
  == Registered custom function ISNULL
  == Registered custom function SET
  == Registered custom function EXISTS
  == Registered custom function IF
  == Registered custom function IFTIME
  == Registered custom function ENV
  == Registered custom function DB
  == Registered custom function DB_EXISTS
  == Registered custom function TIMEOUT
  == Registered custom function LANGUAGE
  == Registered custom function MUSICCLASS
 [chan_iax2.so] => (Inter Asterisk eXchange (Ver 2))
  == Registered custom function IAXPEER
  == Registered application 'IAX2Provision'
  == Manager registered action IAXpeers
  == Manager registered action IAXnetstats
Dec  2 18:47:31 ERROR[16929]: chan_iax2.c:10204 set_config: Unable to load config iax.conf
  == Registered channel type 'IAX2' (Inter Asterisk eXchange Driver (Ver 2))
  == IAX Ready and Listening
  == Loaded firmware 'iaxy.bin'
Dec  2 18:47:31 NOTICE[16929]: iax2-provision.c:515 iax_provision_reload: No IAX provisioning configuration found, IAX provisioning disabled.
 [chan_agent.so] => (Agent Proxy Channel)
  == Registered channel type 'Agent' (Call Agent Proxy Channel)
  == Registered application 'AgentLogin'
  == Registered application 'AgentCallbackLogin'
  == Registered application 'AgentMonitorOutgoing'
  == Manager registered action Agents
  == Manager registered action AgentLogoff
  == Manager registered action AgentCallbackLogin
Dec  2 18:47:31 NOTICE[16929]: chan_agent.c:1053 read_agent_config: No agent configuration found -- agent support disabled
 [chan_skinny.so] => (Skinny Client Control Protocol (Skinny))
Dec  2 18:47:31 NOTICE[16929]: chan_skinny.c:3095 reload_config: Unable to load config skinny.conf, Skinny disabled
  == Registered channel type 'Skinny' (Skinny Client Control Protocol (Skinny))
 [chan_mgcp.so] => (Media Gateway Control Protocol (MGCP))
Dec  2 18:47:31 NOTICE[16929]: chan_mgcp.c:4095 reload_config: Unable to load config mgcp.conf, MGCP disabled
  == Registered channel type 'MGCP' (Media Gateway Control Protocol (MGCP))
 [chan_features.so] => (Feature Proxy Channel)
  == Registered channel type 'Feature' (Feature Proxy Channel Driver)
 [chan_phone.so] => (Linux Telephony API Support)
Dec  2 18:47:32 ERROR[16929]: chan_phone.c:1305 load_module: Unable to load config phone.conf
Dec  2 18:47:32 WARNING[16929]: loader.c:415 __load_resource: chan_phone.so: load_module failed, returning -1
Dec  2 18:47:32 WARNING[16929]: loader.c:555 load_modules: Loading module chan_phone.so failed!


```

Many Thanks!!!

---

