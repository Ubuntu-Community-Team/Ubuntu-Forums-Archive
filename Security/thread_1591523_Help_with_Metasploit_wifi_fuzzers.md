---
title: "Help with Metasploit wifi fuzzers"
date: 2010-10-09
forum: Security
---

### Post by Heil79 on 2010-10-09
I am using a fresh install of Ubuntu 10.04 on a Dell Latitude D620 laptop. I installed Metasploit according to the Ubuntu instructions on the Metasploit website: [http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

When I run the lorcon2 library test on my DLink DWL-AG650 card everything appears to work correctly:

```
/opt/metasploit3/msf3/external/ruby-lorcon2# ruby test.rb wlan1
Checking LORCON version
20091101

Fetching LORCON driver list
{"tuntap"=>
  {"name"=>"tuntap", "description"=>"Linux tuntap virtual interface drivers"},
 "mac80211"=>
  {"name"=>"mac80211",
   "description"=>
    "Linux mac80211 kernel drivers, includes all in-kernel drivers on modern systems"},
 "madwifing"=>
  {"name"=>"madwifing",
   "description"=>"Linux madwifi-ng drivers, deprecated by ath5k and ath9k"}}

Resolving driver by name 'mac80211'
{"name"=>"mac80211",
 "description"=>
  "Linux mac80211 kernel drivers, includes all in-kernel drivers on modern systems"}

Auto-detecting driver for interface wlan0
{"name"=>"mac80211",
 "description"=>
  "Linux mac80211 kernel drivers, includes all in-kernel drivers on modern systems"}

Created LORCON context

Opened as INJMON: wlan1mon
#<Lorcon::Packet:0xb7780c64>
#<Lorcon::Packet:0xb7780c3c>
#<Lorcon::Packet:0xb777ff44>
#<Lorcon::Packet:0xb777ff1c>
^CALL DONE!
```But, when I enter the metasploit console and try to use the fuzzers/wifi/fuzz_beacon module, I get an error:

```
msf > use fuzzers/wifi/fuzz_beacon
msf auxiliary(fuzz_beacon) > set INTERFACE wlan1
INTERFACE => wlan1
msf auxiliary(fuzz_beacon) > run

[-] Auxiliary failed: RuntimeError LORCON could not detect a driver and none specified
[-] Call stack:
[-]   /opt/metasploit3/msf3/lib/msf/core/exploit/lorcon2.rb:70:in `new'
[-]   /opt/metasploit3/msf3/lib/msf/core/exploit/lorcon2.rb:70:in `open_wifi'
[-]   (eval):58:in `run'
[*] Auxiliary module execution completed
```
I have also tried setting the driver explicitly to 'mac80211', 'ath5k', 'madwifi', and 'madwifing'. Each has the same result.

Can anybody suggest what I might be doing wrong? 

Thanks,
PaulH

---

