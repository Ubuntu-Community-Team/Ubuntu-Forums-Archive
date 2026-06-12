---
title: "Asterisk - External Phone Keeps Ringing After I Answer from X-Lite"
date: 2009-11-05
forum: Server Platforms
---

### Post by GraysonPeddie on 2009-11-05
Update: Ah, I should've going into my profile and find my thread. Sorry.

I dial my Asterisk box from my cell phone and when I answer with my X-Lite 3.0 just for testing, I can hear the ringing in my cell phone.

When I disconnect the call from my cell phone, Asterisk signals X-Lite to hang up.

```
Verbosity was 0 and is now 6
  == Using SIP RTP TOS bits 184
  == Using SIP RTP CoS mark 5
    -- Executing [1777xxxxxxx@from-pstn:1] NoOp("SIP/66.193.176.35-0150eed8", "Catch-All DID Match - Found 1777xxxxxxx - You probably want a DID for this.") in new stack
    -- Executing [1777xxxxxxx@from-pstn:2] Goto("SIP/66.193.176.35-0150eed8", "ext-did,s,1") in new stack
    -- Goto (ext-did,s,1)
    -- Executing [s@ext-did:1] Set("SIP/66.193.176.35-0150eed8", "__FROM_DID=s") in new stack
    -- Executing [s@ext-did:2] GotoIf("SIP/66.193.176.35-0150eed8", "1 ?cidok") in new stack
    -- Goto (ext-did,s,4)
    -- Executing [s@ext-did:4] NoOp("SIP/66.193.176.35-0150eed8", "CallerID is "Cell Phone   FL" <1850xxxxxxx>") in new stack
    -- Executing [s@ext-did:5] SetMusicOnHold("SIP/66.193.176.35-0150eed8", "none") in new stack
    -- Executing [s@ext-did:6] Set("SIP/66.193.176.35-0150eed8", "__MOHCLASS=none") in new stack
    -- Executing [s@ext-did:7] Ringing("SIP/66.193.176.35-0150eed8", "") in new stack
    -- Executing [s@ext-did:8] Set("SIP/66.193.176.35-0150eed8", "__CALLINGPRES_SV=allowed_not_screened") in new stack
    -- Executing [s@ext-did:9] Set("SIP/66.193.176.35-0150eed8", "CALLERPRES()=allowed_not_screened") in new stack
    -- Executing [s@ext-did:10] Goto("SIP/66.193.176.35-0150eed8", "from-did-direct,10,1") in new stack
    -- Goto (from-did-direct,10,1)
    -- Executing [10@from-did-direct:1] Set("SIP/66.193.176.35-0150eed8", "__RINGTIMER=45") in new stack
    -- Executing [10@from-did-direct:2] Macro("SIP/66.193.176.35-0150eed8", "exten-vm,10,10") in new stack
    -- Executing [s@macro-exten-vm:1] Macro("SIP/66.193.176.35-0150eed8", "user-callerid") in new stack
    -- Executing [s@macro-user-callerid:1] Set("SIP/66.193.176.35-0150eed8", "AMPUSER=1850xxxxxxx") in new stack
    -- Executing [s@macro-user-callerid:2] GotoIf("SIP/66.193.176.35-0150eed8", "0?report") in new stack
    -- Executing [s@macro-user-callerid:3] ExecIf("SIP/66.193.176.35-0150eed8", "1?Set(REALCALLERIDNUM=1850xxxxxxx)") in new stack
    -- Executing [s@macro-user-callerid:4] Set("SIP/66.193.176.35-0150eed8", "AMPUSER=") in new stack
    -- Executing [s@macro-user-callerid:5] Set("SIP/66.193.176.35-0150eed8", "AMPUSERCIDNAME=") in new stack
    -- Executing [s@macro-user-callerid:6] GotoIf("SIP/66.193.176.35-0150eed8", "1?report") in new stack
    -- Goto (macro-user-callerid,s,10)
    -- Executing [s@macro-user-callerid:10] GotoIf("SIP/66.193.176.35-0150eed8", "0?continue") in new stack
    -- Executing [s@macro-user-callerid:11] Set("SIP/66.193.176.35-0150eed8", "__TTL=64") in new stack
    -- Executing [s@macro-user-callerid:12] GotoIf("SIP/66.193.176.35-0150eed8", "1?continue") in new stack
    -- Goto (macro-user-callerid,s,19)
    -- Executing [s@macro-user-callerid:19] NoOp("SIP/66.193.176.35-0150eed8", "Using CallerID "Cell Phone   FL" <1850xxxxxxx>") in new stack
    -- Executing [s@macro-exten-vm:2] Set("SIP/66.193.176.35-0150eed8", "RingGroupMethod=none") in new stack
    -- Executing [s@macro-exten-vm:3] Set("SIP/66.193.176.35-0150eed8", "VMBOX=10") in new stack
    -- Executing [s@macro-exten-vm:4] Set("SIP/66.193.176.35-0150eed8", "EXTTOCALL=10") in new stack
    -- Executing [s@macro-exten-vm:5] Set("SIP/66.193.176.35-0150eed8", "CFUEXT=") in new stack
    -- Executing [s@macro-exten-vm:6] Set("SIP/66.193.176.35-0150eed8", "CFBEXT=") in new stack
    -- Executing [s@macro-exten-vm:7] Set("SIP/66.193.176.35-0150eed8", "RT=45") in new stack
    -- Executing [s@macro-exten-vm:8] Macro("SIP/66.193.176.35-0150eed8", "record-enable,10,IN") in new stack
    -- Executing [s@macro-record-enable:1] GotoIf("SIP/66.193.176.35-0150eed8", "1?check") in new stack
    -- Goto (macro-record-enable,s,4)
    -- Executing [s@macro-record-enable:4] AGI("SIP/66.193.176.35-0150eed8", "recordingcheck,20091104-073351,1257338031.4") in new stack
    -- Launched AGI Script /var/lib/asterisk/agi-bin/recordingcheck
 recordingcheck,20091104-073351,1257338031.4: Inbound recording not enabled
    -- <SIP/66.193.176.35-0150eed8>AGI Script recordingcheck completed, returning 0
    -- Executing [s@macro-record-enable:5] MacroExit("SIP/66.193.176.35-0150eed8", "") in new stack
    -- Executing [s@macro-exten-vm:9] Macro("SIP/66.193.176.35-0150eed8", "dial,45,tr,10") in new stack
    -- Executing [s@macro-dial:1] GotoIf("SIP/66.193.176.35-0150eed8", "0?dial") in new stack
    -- Executing [s@macro-dial:2] SetMusicOnHold("SIP/66.193.176.35-0150eed8", "none") in new stack
    -- Executing [s@macro-dial:3] AGI("SIP/66.193.176.35-0150eed8", "dialparties.agi") in new stack
    -- Launched AGI Script /var/lib/asterisk/agi-bin/dialparties.agi
 dialparties.agi: Starting New Dialparties.agi
  == Manager 'admin' logged on from 127.0.0.1
 dialparties.agi: Caller ID name is 'Cell Phone   FL' number is '1850xxxxxxx'
       > dialparties.agi: USE_CONFIRMATION:  'FALSE'
       > dialparties.agi: RINGGROUP_INDEX:   ''
 dialparties.agi: Methodology of ring is  'none'
    -- dialparties.agi: Added extension 10 to extension map
       > dialparties.agi: Extension 10 has call screening off
    -- dialparties.agi: Extension 10 cf is disabled
    -- dialparties.agi: Extension 10 do not disturb is disabled
       > dialparties.agi: extnum 10 has:  cw: 1; hascfb: 0 [] hascfu: 0 []
       > dialparties.agi: ExtensionState: 0
    -- dialparties.agi: dbset CALLTRACE/10 to 1850xxxxxxx
    -- dialparties.agi: Filtered ARG3: 10
  == Manager 'admin' logged off from 127.0.0.1
    -- <SIP/66.193.176.35-0150eed8>AGI Script dialparties.agi completed, returning 0
    -- Executing [s@macro-dial:7] Dial("SIP/66.193.176.35-0150eed8", "SIP/10,45,tr") in new stack
  == Using SIP RTP TOS bits 184
  == Using SIP RTP CoS mark 5
    -- Called 10
    -- SIP/10-01508d58 is ringing
       > doing dnsmgr_lookup for 'callcentric.com'
       > ast_get_srv: SRV lookup for '_sip._UDP.callcentric.com' mapped to host alpha7.callcentric.com, port 5080
       > doing dnsmgr_lookup for 'callcentric.com'
       > ast_get_srv: SRV lookup for '_sip._UDP.callcentric.com' mapped to host alpha6.callcentric.com, port 5080
    -- SIP/10-01508d58 answered SIP/66.193.176.35-0150eed8
    -- Executing [h@macro-dial:1] Macro("SIP/66.193.176.35-0150eed8", "hangupcall") in new stack
    -- Executing [s@macro-hangupcall:1] ResetCDR("SIP/66.193.176.35-0150eed8", "w") in new stack
    -- Executing [s@macro-hangupcall:2] NoCDR("SIP/66.193.176.35-0150eed8", "") in new stack
    -- Executing [s@macro-hangupcall:3] GotoIf("SIP/66.193.176.35-0150eed8", "1?skiprg") in new stack
    -- Goto (macro-hangupcall,s,6)
    -- Executing [s@macro-hangupcall:6] GotoIf("SIP/66.193.176.35-0150eed8", "1?skipblkvm") in new stack
    -- Goto (macro-hangupcall,s,9)
    -- Executing [s@macro-hangupcall:9] GotoIf("SIP/66.193.176.35-0150eed8", "1?theend") in new stack
    -- Goto (macro-hangupcall,s,11)
    -- Executing [s@macro-hangupcall:11] Hangup("SIP/66.193.176.35-0150eed8", "") in new stack
  == Spawn extension (macro-hangupcall, s, 11) exited non-zero on 'SIP/66.193.176.35-0150eed8' in macro 'hangupcall'
  == Spawn extension (macro-dial, h, 1) exited non-zero on 'SIP/66.193.176.35-0150eed8'
  == Spawn extension (macro-dial, s, 7) exited non-zero on 'SIP/66.193.176.35-0150eed8' in macro 'dial'
  == Spawn extension (macro-exten-vm, s, 9) exited non-zero on 'SIP/66.193.176.35-0150eed8' in macro 'exten-vm'
  == Spawn extension (from-did-direct, 10, 2) exited non-zero on 'SIP/66.193.176.35-0150eed8'
```

When I dial my Asterisk box from my cell phone and chose to hang up the phone from X-Lite, my cell phone keeps ringing.

```
  == Using SIP RTP TOS bits 184
  == Using SIP RTP CoS mark 5
    -- Executing [1777xxxxxxx@from-pstn:1] NoOp("SIP/66.193.176.35-01508aa8", "Catch-All DID Match - Found 1777xxxxxxx - You probably want a DID for this.") in new stack
    -- Executing [1777xxxxxxx@from-pstn:2] Goto("SIP/66.193.176.35-01508aa8", "ext-did,s,1") in new stack
    -- Goto (ext-did,s,1)
    -- Executing [s@ext-did:1] Set("SIP/66.193.176.35-01508aa8", "__FROM_DID=s") in new stack
    -- Executing [s@ext-did:2] GotoIf("SIP/66.193.176.35-01508aa8", "1 ?cidok") in new stack
    -- Goto (ext-did,s,4)
    -- Executing [s@ext-did:4] NoOp("SIP/66.193.176.35-01508aa8", "CallerID is "Cell Phone   FL" <1850xxxxxxx>") in new stack
    -- Executing [s@ext-did:5] SetMusicOnHold("SIP/66.193.176.35-01508aa8", "none") in new stack
    -- Executing [s@ext-did:6] Set("SIP/66.193.176.35-01508aa8", "__MOHCLASS=none") in new stack
    -- Executing [s@ext-did:7] Ringing("SIP/66.193.176.35-01508aa8", "") in new stack
    -- Executing [s@ext-did:8] Set("SIP/66.193.176.35-01508aa8", "__CALLINGPRES_SV=allowed_not_screened") in new stack
    -- Executing [s@ext-did:9] Set("SIP/66.193.176.35-01508aa8", "CALLERPRES()=allowed_not_screened") in new stack
    -- Executing [s@ext-did:10] Goto("SIP/66.193.176.35-01508aa8", "from-did-direct,10,1") in new stack
    -- Goto (from-did-direct,10,1)
    -- Executing [10@from-did-direct:1] Set("SIP/66.193.176.35-01508aa8", "__RINGTIMER=45") in new stack
    -- Executing [10@from-did-direct:2] Macro("SIP/66.193.176.35-01508aa8", "exten-vm,10,10") in new stack
    -- Executing [s@macro-exten-vm:1] Macro("SIP/66.193.176.35-01508aa8", "user-callerid") in new stack
    -- Executing [s@macro-user-callerid:1] Set("SIP/66.193.176.35-01508aa8", "AMPUSER=1850xxxxxxx") in new stack
    -- Executing [s@macro-user-callerid:2] GotoIf("SIP/66.193.176.35-01508aa8", "0?report") in new stack
    -- Executing [s@macro-user-callerid:3] ExecIf("SIP/66.193.176.35-01508aa8", "1?Set(REALCALLERIDNUM=1850xxxxxxx)") in new stack
    -- Executing [s@macro-user-callerid:4] Set("SIP/66.193.176.35-01508aa8", "AMPUSER=") in new stack
    -- Executing [s@macro-user-callerid:5] Set("SIP/66.193.176.35-01508aa8", "AMPUSERCIDNAME=") in new stack
    -- Executing [s@macro-user-callerid:6] GotoIf("SIP/66.193.176.35-01508aa8", "1?report") in new stack
    -- Goto (macro-user-callerid,s,10)
    -- Executing [s@macro-user-callerid:10] GotoIf("SIP/66.193.176.35-01508aa8", "0?continue") in new stack
    -- Executing [s@macro-user-callerid:11] Set("SIP/66.193.176.35-01508aa8", "__TTL=64") in new stack
    -- Executing [s@macro-user-callerid:12] GotoIf("SIP/66.193.176.35-01508aa8", "1?continue") in new stack
    -- Goto (macro-user-callerid,s,19)
    -- Executing [s@macro-user-callerid:19] NoOp("SIP/66.193.176.35-01508aa8", "Using CallerID "Cell Phone   FL" <1850xxxxxxx>") in new stack
    -- Executing [s@macro-exten-vm:2] Set("SIP/66.193.176.35-01508aa8", "RingGroupMethod=none") in new stack
    -- Executing [s@macro-exten-vm:3] Set("SIP/66.193.176.35-01508aa8", "VMBOX=10") in new stack
    -- Executing [s@macro-exten-vm:4] Set("SIP/66.193.176.35-01508aa8", "EXTTOCALL=10") in new stack
    -- Executing [s@macro-exten-vm:5] Set("SIP/66.193.176.35-01508aa8", "CFUEXT=") in new stack
    -- Executing [s@macro-exten-vm:6] Set("SIP/66.193.176.35-01508aa8", "CFBEXT=") in new stack
    -- Executing [s@macro-exten-vm:7] Set("SIP/66.193.176.35-01508aa8", "RT=45") in new stack
    -- Executing [s@macro-exten-vm:8] Macro("SIP/66.193.176.35-01508aa8", "record-enable,10,IN") in new stack
    -- Executing [s@macro-record-enable:1] GotoIf("SIP/66.193.176.35-01508aa8", "1?check") in new stack
    -- Goto (macro-record-enable,s,4)
    -- Executing [s@macro-record-enable:4] AGI("SIP/66.193.176.35-01508aa8", "recordingcheck,20091104-075717,1257339437.6") in new stack
    -- Launched AGI Script /var/lib/asterisk/agi-bin/recordingcheck
 recordingcheck,20091104-075717,1257339437.6: Inbound recording not enabled
    -- <SIP/66.193.176.35-01508aa8>AGI Script recordingcheck completed, returning 0
    -- Executing [s@macro-record-enable:5] MacroExit("SIP/66.193.176.35-01508aa8", "") in new stack
    -- Executing [s@macro-exten-vm:9] Macro("SIP/66.193.176.35-01508aa8", "dial,45,tr,10") in new stack
    -- Executing [s@macro-dial:1] GotoIf("SIP/66.193.176.35-01508aa8", "0?dial") in new stack
    -- Executing [s@macro-dial:2] SetMusicOnHold("SIP/66.193.176.35-01508aa8", "none") in new stack
    -- Executing [s@macro-dial:3] AGI("SIP/66.193.176.35-01508aa8", "dialparties.agi") in new stack
    -- Launched AGI Script /var/lib/asterisk/agi-bin/dialparties.agi
 dialparties.agi: Starting New Dialparties.agi
  == Manager 'admin' logged on from 127.0.0.1
 dialparties.agi: Caller ID name is 'Cell Phone   FL' number is '1850xxxxxxx'
       > dialparties.agi: USE_CONFIRMATION:  'FALSE'
       > dialparties.agi: RINGGROUP_INDEX:   ''
 dialparties.agi: Methodology of ring is  'none'
    -- dialparties.agi: Added extension 10 to extension map
       > dialparties.agi: Extension 10 has call screening off
    -- dialparties.agi: Extension 10 cf is disabled
    -- dialparties.agi: Extension 10 do not disturb is disabled
       > dialparties.agi: extnum 10 has:  cw: 1; hascfb: 0 [] hascfu: 0 []
       > dialparties.agi: ExtensionState: 0
    -- dialparties.agi: dbset CALLTRACE/10 to 1850xxxxxxx
    -- dialparties.agi: Filtered ARG3: 10
  == Manager 'admin' logged off from 127.0.0.1
    -- <SIP/66.193.176.35-01508aa8>AGI Script dialparties.agi completed, returning 0
    -- Executing [s@macro-dial:7] Dial("SIP/66.193.176.35-01508aa8", "SIP/10,45,tr") in new stack
  == Using SIP RTP TOS bits 184
  == Using SIP RTP CoS mark 5
    -- Called 10CLI> 
    -- SIP/10-014fef08 is ringing
       > doing dnsmgr_lookup for 'callcentric.com'
       > ast_get_srv: SRV lookup for '_sip._UDP.callcentric.com' mapped to host alpha1.callcentric.com, port 5080
       > doing dnsmgr_lookup for 'callcentric.com'
       > ast_get_srv: SRV lookup for '_sip._UDP.callcentric.com' mapped to host alpha7.callcentric.com, port 5080
    -- SIP/10-014fef08 answered SIP/66.193.176.35-01508aa8
    -- Executing [h@macro-dial:1] Macro("SIP/66.193.176.35-01508aa8", "hangupcall") in new stack
    -- Executing [s@macro-hangupcall:1] ResetCDR("SIP/66.193.176.35-01508aa8", "w") in new stack
    -- Executing [s@macro-hangupcall:2] NoCDR("SIP/66.193.176.35-01508aa8", "") in new stack
    -- Executing [s@macro-hangupcall:3] GotoIf("SIP/66.193.176.35-01508aa8", "1?skiprg") in new stack
    -- Goto (macro-hangupcall,s,6)
    -- Executing [s@macro-hangupcall:6] GotoIf("SIP/66.193.176.35-01508aa8", "1?skipblkvm") in new stack
    -- Goto (macro-hangupcall,s,9)
    -- Executing [s@macro-hangupcall:9] GotoIf("SIP/66.193.176.35-01508aa8", "1?theend") in new stack
    -- Goto (macro-hangupcall,s,11)
    -- Executing [s@macro-hangupcall:11] Hangup("SIP/66.193.176.35-01508aa8", "") in new stack
  == Spawn extension (macro-hangupcall, s, 11) exited non-zero on 'SIP/66.193.176.35-01508aa8' in macro 'hangupcall'
  == Spawn extension (macro-dial, h, 1) exited non-zero on 'SIP/66.193.176.35-01508aa8'
  == Spawn extension (macro-dial, s, 7) exited non-zero on 'SIP/66.193.176.35-01508aa8' in macro 'dial'
  == Spawn extension (macro-exten-vm, s, 9) exited non-zero on 'SIP/66.193.176.35-01508aa8' in macro 'exten-vm'
  == Spawn extension (from-did-direct, 10, 2) exited non-zero on 'SIP/66.193.176.35-01508aa8'
```

Connection from Internet to Computer:

Cable Modem (DHCP) -> Ubuntu 9.10 as router -> Switch -> Computer

sip.conf

...
...
...
context=from-pstn
srvlookup=yes;

CallCentric (trunk):

```
host=callcentric.com
fromdomain=callcentric.com
username=1777xxxxxxx
fromuser=1777xxxxxxx
authuser=1777xxxxxxx
secret=mysecret
type=peer
insecure=port,invite
context=from-pstn
```

I dial a 407 phone number, which is assigned to my CallCentric account.

I use Webmin to configure the firewall and I don't know where it's at for copying from the file to here, but I have TCP 5060 and UDP 10000:20000 opened through eth0 and I filter out SYN packets (port scanning) and ICMP request.

I can make outgoing calls just fine. Any solutions to my problem?

---

### Post by GraysonPeddie on 2009-11-06
I looked through the list of threads in my profile and I didn't see any other double-posted ones (same forum), but oh well...

I made so many connections from my pre-paid cell phone to my Asterisk to test to make sure it's working, since each call is 25 cents... :( But that's not the point even though I've got to be careful when testing Asterisk externally.

Okay, so I went to the DID section of FreePBX and when I change from Extension (Grayson Peddie - 10) to Voicemail (Grayson Peddie - 10), I hear silence from my cell phone. Plus, whether I have "Signal RINGING" enabled or not still does not matter. It will just continue to ring from my cell phone specified in my extension's ring time.

Let me give you an example of what's going on when someone is trying to call me: Okay, so my mom dialed my phone number and it connects to Asterisk to ring my softphone. I answer the call, but my mom's cell phone keeps ringing. Because of that, if I immediately call her back, I'll immediately get sent to voicemail and will have to wait for the reminder of the ring time to pass to call her back. So for my experience of switching to voicemail from extension in the DID section, my mom will hear silence in my voicemail.

My FreePBX is not behind a NAT, as it's within a router. My computer is behind my Linux firewall using iptables (I use Webmin). Ports have already been opened: TCP: 5060, UDP: 5060, UDP: 10001-20000 (RTP).

Update: Never mind my entire thread. Although I love FreePBX+Asterisk, it is pretty much easier to go with 3CX for Windows with less features than Asterisk+FreePBX, but I'd not waste too much time in my hands, so I'm better off not having software PBX at all.

I'd like to install Trixbox, but I don't have a dedicated server for that. Neither if I want to format my hard drive just to install Trixbox. Compiling patched ZapTel does not seem to help when it comes to having a dummy driver for Asterisk, but gee-- just give me a binary package that comes with everything I need and that I don't have to worry about erasing my hard drive, just like 3CX allows me to install the phone system for Windows, and I'll be off and running in just a few minutes... :( I dislike compiling software anymore... :(

Sorry, I don't mean to bring up Windows vs Linux when it comes to which phone systems are the easiest to install and configure. *sigh* :(

---

