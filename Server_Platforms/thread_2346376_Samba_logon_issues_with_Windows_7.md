---
title: "Samba logon issues with Windows 7"
date: 2016-12-14
forum: Server Platforms
---

### Post by manduck2 on 2016-12-14
Hi all! I have a samba 3.6.3 domain that new Windows 7 machine are unable to logon to. They're getting a 'no logon server available error' when logging on and there's a 'RPC server is unavailable' error in the event logs. They are binding to the domain fine initially though.

I have other Windows 7 computer that have been working for a while, and there's no problem with these logging on. However, I did un-bind and then re-bind one of them to the domain, and it's now getting the same error when trying to logon.

I'm a bit stuck as to why this would just to happening for new computers. Any help would be greatly appreciated.

Here's the output of log.nmbd, I thought it was a bit strange that the 'user_name' line is blank. Could that be something to do with it?


```
[2016/12/13 16:52:16,  4] nmbd/nmbd_packets.c:1294(process_dgram)
  process_dgram: datagram from W431B<00> to GATSBY<1c> IP 192.168.213.16 for \MAILSLOT\NET\NETLOGON of type 18 len=84
[2016/12/13 16:52:16,  1] ../librpc/ndr/ndr.c:247(ndr_print_debug)
       &request: struct nbt_netlogon_packet
          command                  : LOGON_SAM_LOGON_REQUEST (18)
          req                      : union nbt_netlogon_request(case 18)
          logon: struct NETLOGON_SAM_LOGON_REQUEST
              request_count            : 0x0000 (0)
              computer_name            : 'W431B'
              user_name                : ''
              mailslot_name            : '\MAILSLOT\NET\GETDC501'
              acct_control             : 0x00000000 (0)
                     0: ACB_DISABLED             
                     0: ACB_HOMDIRREQ            
                     0: ACB_PWNOTREQ             
                     0: ACB_TEMPDUP              
                     0: ACB_NORMAL               
                     0: ACB_MNS                  
                     0: ACB_DOMTRUST             
                     0: ACB_WSTRUST              
                     0: ACB_SVRTRUST             
                     0: ACB_PWNOEXP              
                     0: ACB_AUTOLOCK             
                     0: ACB_ENC_TXT_PWD_ALLOWED  
                     0: ACB_SMARTCARD_REQUIRED   
                     0: ACB_TRUSTED_FOR_DELEGATION
                     0: ACB_NOT_DELEGATED        
                     0: ACB_USE_DES_KEY_ONLY     
                     0: ACB_DONT_REQUIRE_PREAUTH 
                     0: ACB_PW_EXPIRED           
                     0: ACB_TRUSTED_TO_AUTHENTICATE_FOR_DELEGATION
                     0: ACB_NO_AUTH_DATA_REQD    
                     0: ACB_PARTIAL_SECRETS_ACCOUNT
                     0: ACB_USE_AES_KEYS         
              sid_size                 : 0x00000018 (24)
              _pad                     : DATA_BLOB length=3
  [0000] 00 00 00                                          ... 
              sid                      : S-1-5-21-3267188772-4123625671-2941533749
              nt_version               : 0x0000000b (11)
                     1: NETLOGON_NT_VERSION_1    
                     1: NETLOGON_NT_VERSION_5    
                     0: NETLOGON_NT_VERSION_5EX  
                     1: NETLOGON_NT_VERSION_5EX_WITH_IP
                     0: NETLOGON_NT_VERSION_WITH_CLOSEST_SITE
                     0: NETLOGON_NT_VERSION_AVOID_NT4EMUL
                     0: NETLOGON_NT_VERSION_PDC  
                     0: NETLOGON_NT_VERSION_IP   
                     0: NETLOGON_NT_VERSION_LOCAL
                     0: NETLOGON_NT_VERSION_GC   
              lmnt_token               : 0xffff (65535)
              lm20_token               : 0xffff (65535)
[2016/12/13 16:52:16,  4] nmbd/nmbd_processlogon.c:362(process_logon_packet)
  process_logon_packet: Logon from 192.168.213.16: code = 0x12
[2016/12/13 16:52:16,  5] nmbd/nmbd_processlogon.c:480(process_logon_packet)
  process_logon_packet: LOGON_SAM_LOGON_REQUEST request from W431B(192.168.213.16) for , returning logon svr \\NFS-MAIN domain GATSBY code 13 token=ffff
[2016/12/13 16:52:16,  1] ../librpc/ndr/ndr.c:247(ndr_print_debug)
       &nt4: struct NETLOGON_SAM_LOGON_RESPONSE_NT40
          command                  : LOGON_SAM_LOGON_RESPONSE (19)
          pdc_name                 : '\\NFS-MAIN'
          user_name                : ''
          domain_name              : 'GATSBY'
          nt_version               : 0x00000001 (1)
                 1: NETLOGON_NT_VERSION_1    
                 0: NETLOGON_NT_VERSION_5    
                 0: NETLOGON_NT_VERSION_5EX  
                 0: NETLOGON_NT_VERSION_5EX_WITH_IP
                 0: NETLOGON_NT_VERSION_WITH_CLOSEST_SITE
                 0: NETLOGON_NT_VERSION_AVOID_NT4EMUL
                 0: NETLOGON_NT_VERSION_PDC  
                 0: NETLOGON_NT_VERSION_IP   
                 0: NETLOGON_NT_VERSION_LOCAL
                 0: NETLOGON_NT_VERSION_GC   
          lmnt_token               : 0xffff (65535)
          lm20_token               : 0xffff (65535)
[2016/12/13 16:52:16,  3] nmbd/nmbd_processlogon.c:620(process_logon_packet)
  process_logon_packet: processing delayed initial logon reply for client W431B(192.168.213.16)
[2016/12/13 16:52:16,  4] nmbd/nmbd_packets.c:2114(send_mailslot)
  send_mailslot: Sending to mailslot \MAILSLOT\NET\GETDC501 from NFS-MAIN<00> IP 192.168.213.122 to W431B<00> IP 192.168.213.16
[2016/12/13 16:52:16,  4] nmbd/nmbd_packets.c:116(debug_browse_data)
  debug_browse_data():
    0 char ..\.\.N.F.S.-.M. hex 13 00 5c 00 5c 00 4e 00 46 00 53 00 2d 00 4d 00
   10 char A.I.N.....G.A.T. hex 41 00 49 00 4e 00 00 00 00 00 47 00 41 00 54 00
   20 char S.B.Y........... hex 53 00 42 00 59 00 00 00 01 00 00 00 ff ff ff ff
[2016/12/13 16:52:16,  5] libsmb/nmblib.c:841(send_udp)
  Sending a packet of len 222 to (192.168.213.16) on port 138
```

---

