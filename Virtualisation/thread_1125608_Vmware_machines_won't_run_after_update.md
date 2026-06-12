---
title: "Vmware machines won't run after update"
date: 2009-04-14
forum: Virtualisation
---

### Post by Julian David Pitt on 2009-04-14
I  have recently updated Vmware server from 1.0.6 to 1.0.8. Since this none of my virtual machines will now run. Is there anything I need to do to rectify this please.

---

### Post by Dedoimedo on 2009-04-15
Could you provide a specific error you see?
Second, in the server console, did you right-click on the machines > upgrade?

Lastly, can you please open one of the .vmx config files and tell me what it shows in the first few lines. You can do this using head in the command line, or if you're uncomfortable with it, just open in text editor and paste the first 10 lines or so. I'm interested in the version thingie.

Something like:

config.version = "8"
virtualHW.version = "4"

Cheers,
Dedoimedo

---

### Post by Julian David Pitt on 2009-04-15
> did you right-click on the machines > upgrade?
When I try this I receive```
Cannot upgrade virtual machine: The virtual machine's hardware is up-to-date and does not need to be upgraded
```.I should point out that I managed to run a Linux VM ok last night,the only real snag was that the screen kept flickering and all the text would disappear from each window. This happened about every 30 seconds or so. I am none too sure about how to use head in the command line and all I can find in the vmx files directory are some log files and nothing in the way of config files. I have found that I am running version 1.0.8 build-126538 if that is any help?

---

### Post by Dedoimedo on 2009-04-16
Can you please start vmware from the command line. That way, you'll get the exact error on the command line. Please copy paste it here.

To use head, it goes like this:

```
head <filename>
```

I don't know where you keep the config files, but .vmx file should be plain visible.

Dedoimedo

---

### Post by Julian David Pitt on 2009-04-17
> Can you please start vmware from the command line. That way, you'll get the exact error on the command line. Please copy paste it here.

This is what I get when started from the command line:

```
julian@Hardy:~$ sudo vmware
[sudo] password for julian: 
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'                
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory                               
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings       
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory                                    
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name          
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory                                     
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory                                                                
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default          
(null): file ../../libview-0.5.6/libview/autoDrawer.c: line 213 (ViewAutoDrawerUpdate): assertion failed: (grabbed)                               
julian@Hardy:~$ vmware                                                   
Unable to alloc client: Cannot open file "/home/julian/.vmware/preferences": Permission denied.

VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/julian/.vmware/preferences": Permission denied.

A log file is available in "/tmp/vmware-julian/ui-8760.log".  Please request support and include the contents of the log file.
To collect files to submit to VMware support, run vm-support
```

If I then run vm-support I get:

```
vm-support.10110/proc/6427/fdinfo/9                                      
vm-support.10110/proc/6427/fdinfo/14                                     
vm-support.10110/proc/6427/fdinfo/12                                     
vm-support.10110/proc/6427/fdinfo/7                                      
vm-support.10110/proc/6427/fdinfo/17                                     
vm-support.10110/proc/6427/fdinfo/4                                      
vm-support.10110/proc/6427/fdinfo/18                                     
vm-support.10110/proc/6427/fdinfo/2                                      
vm-support.10110/proc/6427/fdinfo/11                                     
vm-support.10110/proc/6427/fdinfo/20                                     
vm-support.10110/proc/6427/fdinfo/19                                     
vm-support.10110/proc/6427/fdinfo/15                                     
vm-support.10110/proc/6427/fdinfo/1                                      
vm-support.10110/proc/6427/fdinfo/10                                     
vm-support.10110/proc/6427/loginuid                                      
vm-support.10110/proc/6427/environ                                       
vm-support.10110/proc/6427/coredump_filter                               
vm-support.10110/proc/6427/oom_score                                     
vm-support.10110/proc/6427/statm                                         
vm-support.10110/proc/6427/pagemap                                       
vm-support.10110/proc/6427/auxv                                          
vm-support.10110/proc/6427/clear_refs                                    
vm-support.10110/proc/6427/wchan                                         
vm-support.10110/proc/6427/mountinfo                                     
vm-support.10110/proc/6427/cpuset                                        
vm-support.10110/proc/6427/io                                            
vm-support.10110/proc/6427/maps                                          
vm-support.10110/proc/6427/cgroup                                        
vm-support.10110/proc/6427/oom_adj                                       
vm-support.10110/proc/6427/mountstats                                    
vm-support.10110/proc/6427/status                                        
vm-support.10110/proc/6427/schedstat                                     
vm-support.10110/proc/6427/cmdline                                       
vm-support.10110/proc/6427/latency                                       
vm-support.10110/proc/6427/limits                                        
vm-support.10110/proc/6427/net/                                          
vm-support.10110/proc/6427/net/if_inet6                                  
vm-support.10110/proc/6427/net/dev_mcast                                 
vm-support.10110/proc/6427/net/dev_snmp6/                                
vm-support.10110/proc/6427/net/dev_snmp6/eth0                            
vm-support.10110/proc/6427/net/dev_snmp6/vmnet8                          
vm-support.10110/proc/6427/net/dev_snmp6/wmaster0                        
vm-support.10110/proc/6427/net/dev_snmp6/irda0                           
vm-support.10110/proc/6427/net/dev_snmp6/wlan0                           
vm-support.10110/proc/6427/net/dev_snmp6/lo                              
vm-support.10110/proc/6427/net/dev_snmp6/vmnet1                          
vm-support.10110/proc/6427/net/netstat                                   
vm-support.10110/proc/6427/net/ip_mr_vif                                 
vm-support.10110/proc/6427/net/rt_cache                                  
vm-support.10110/proc/6427/net/route                                     
vm-support.10110/proc/6427/net/snmp                                      
vm-support.10110/proc/6427/net/igmp6                                     
vm-support.10110/proc/6427/net/mcfilter                                  
vm-support.10110/proc/6427/net/netfilter/                                
vm-support.10110/proc/6427/net/netfilter/nf_log                          
vm-support.10110/proc/6427/net/netfilter/nf_queue                        
vm-support.10110/proc/6427/net/ptype                                     
vm-support.10110/proc/6427/net/netlink                                   
vm-support.10110/proc/6427/net/ndiswrapper/                              
vm-support.10110/proc/6427/net/ndiswrapper/debug                         
vm-support.10110/proc/6427/net/softnet_stat                              
vm-support.10110/proc/6427/net/protocols                                 
vm-support.10110/proc/6427/net/igmp                                      
vm-support.10110/proc/6427/net/rt6_stats                                 
vm-support.10110/proc/6427/net/udplite6                                  
vm-support.10110/proc/6427/net/udplite                                   
vm-support.10110/proc/6427/net/tcp6                                      
vm-support.10110/proc/6427/net/sockstat6                                 
vm-support.10110/proc/6427/net/arp                                       
vm-support.10110/proc/6427/net/unix                                      
vm-support.10110/proc/6427/net/udp6                                      
vm-support.10110/proc/6427/net/tcp                                       
vm-support.10110/proc/6427/net/snmp6                                     
vm-support.10110/proc/6427/net/anycast6                                  
vm-support.10110/proc/6427/net/mcfilter6                                 
vm-support.10110/proc/6427/net/packet                                    
vm-support.10110/proc/6427/net/psched                                    
vm-support.10110/proc/6427/net/connector                                 
vm-support.10110/proc/6427/net/ip_tables_targets                         
vm-support.10110/proc/6427/net/atm/                                      
vm-support.10110/proc/6427/net/atm/pvc                                   
vm-support.10110/proc/6427/net/atm/vc                                    
vm-support.10110/proc/6427/net/atm/devices                               
vm-support.10110/proc/6427/net/atm/arp                                   
vm-support.10110/proc/6427/net/atm/svc                                   
vm-support.10110/proc/6427/net/dev                                       
vm-support.10110/proc/6427/net/raw6                                      
vm-support.10110/proc/6427/net/ip_tables_names                           
vm-support.10110/proc/6427/net/sockstat                                  
vm-support.10110/proc/6427/net/ip_tables_matches                         
vm-support.10110/proc/6427/net/udp                                       
vm-support.10110/proc/6427/net/ip6_flowlabel                             
vm-support.10110/proc/6427/net/irda/                                     
vm-support.10110/proc/6427/net/irda/irias                                
vm-support.10110/proc/6427/net/irda/irlmp                                
vm-support.10110/proc/6427/net/irda/irttp                                
vm-support.10110/proc/6427/net/irda/discovery                            
vm-support.10110/proc/6427/net/irda/irlap                                
vm-support.10110/proc/6427/net/rt_acct                                   
vm-support.10110/proc/6427/net/raw                                       
vm-support.10110/proc/6427/net/wireless                                  
vm-support.10110/proc/6427/net/ip_mr_cache                               
vm-support.10110/proc/6427/net/stat/                                     
vm-support.10110/proc/6427/net/stat/arp_cache                            
vm-support.10110/proc/6427/net/stat/rt_cache                             
vm-support.10110/proc/6427/net/stat/ndisc_cache                          
vm-support.10110/proc/6427/net/stat/clip_arp_cache                       
vm-support.10110/proc/6427/net/ipv6_route                                
vm-support.10110/proc/6427/net/tr_rif                                    
vm-support.10110/proc/6427/task/                                         
vm-support.10110/proc/6427/task/6427/                                    
vm-support.10110/proc/6427/task/6427/smaps                               
vm-support.10110/proc/6427/task/6427/attr/                               
vm-support.10110/proc/6427/task/6427/attr/prev                           
vm-support.10110/proc/6427/task/6427/attr/keycreate                      
vm-support.10110/proc/6427/task/6427/attr/exec                           
vm-support.10110/proc/6427/task/6427/attr/fscreate                       
vm-support.10110/proc/6427/task/6427/attr/sockcreate                     
vm-support.10110/proc/6427/task/6427/attr/current                        
vm-support.10110/proc/6427/task/6427/sched                               
vm-support.10110/proc/6427/task/6427/sessionid                           
vm-support.10110/proc/6427/task/6427/fdinfo/                             
vm-support.10110/proc/6427/task/6427/fdinfo/3                            
vm-support.10110/proc/6427/task/6427/fdinfo/16                           
vm-support.10110/proc/6427/task/6427/fdinfo/5                            
vm-support.10110/proc/6427/task/6427/fdinfo/8                            
vm-support.10110/proc/6427/task/6427/fdinfo/6                            
vm-support.10110/proc/6427/task/6427/fdinfo/13                           
vm-support.10110/proc/6427/task/6427/fdinfo/0                            
vm-support.10110/proc/6427/task/6427/fdinfo/9                            
vm-support.10110/proc/6427/task/6427/fdinfo/14                           
vm-support.10110/proc/6427/task/6427/fdinfo/12                           
vm-support.10110/proc/6427/task/6427/fdinfo/7                            
vm-support.10110/proc/6427/task/6427/fdinfo/17                           
vm-support.10110/proc/6427/task/6427/fdinfo/4                            
vm-support.10110/proc/6427/task/6427/fdinfo/18                           
vm-support.10110/proc/6427/task/6427/fdinfo/2                            
vm-support.10110/proc/6427/task/6427/fdinfo/11                           
vm-support.10110/proc/6427/task/6427/fdinfo/20                           
vm-support.10110/proc/6427/task/6427/fdinfo/19                           
vm-support.10110/proc/6427/task/6427/fdinfo/15                           
vm-support.10110/proc/6427/task/6427/fdinfo/1                            
vm-support.10110/proc/6427/task/6427/fdinfo/10                           
vm-support.10110/proc/6427/task/6427/loginuid                            
vm-support.10110/proc/6427/task/6427/environ                             
vm-support.10110/proc/6427/task/6427/oom_score                           
vm-support.10110/proc/6427/task/6427/statm                               
vm-support.10110/proc/6427/task/6427/pagemap                             
vm-support.10110/proc/6427/task/6427/auxv                                
vm-support.10110/proc/6427/task/6427/clear_refs                          
vm-support.10110/proc/6427/task/6427/wchan                               
vm-support.10110/proc/6427/task/6427/mountinfo                           
vm-support.10110/proc/6427/task/6427/cpuset                              
vm-support.10110/proc/6427/task/6427/io                                  
vm-support.10110/proc/6427/task/6427/maps                                
vm-support.10110/proc/6427/task/6427/cgroup                              
vm-support.10110/proc/6427/task/6427/oom_adj                             
vm-support.10110/proc/6427/task/6427/status                              
vm-support.10110/proc/6427/task/6427/schedstat                           
vm-support.10110/proc/6427/task/6427/cmdline                             
vm-support.10110/proc/6427/task/6427/latency                             
vm-support.10110/proc/6427/task/6427/limits                              
vm-support.10110/proc/6427/task/6427/mounts                              
vm-support.10110/proc/6427/task/6427/stat                                
vm-support.10110/proc/6427/task/6427/mem                                 
vm-support.10110/proc/6427/mounts                                        
vm-support.10110/proc/6427/stat                                          
vm-support.10110/proc/6427/mem                                           
vm-support.10110/proc/stat                                               
vm-support.10110/proc/4123/                                              
vm-support.10110/proc/4123/smaps                                         
vm-support.10110/proc/4123/attr/                                         
vm-support.10110/proc/4123/attr/prev                                     
vm-support.10110/proc/4123/attr/keycreate                                
vm-support.10110/proc/4123/attr/exec                                     
vm-support.10110/proc/4123/attr/fscreate                                 
vm-support.10110/proc/4123/attr/sockcreate                               
vm-support.10110/proc/4123/attr/current                                  
vm-support.10110/proc/4123/sched                                         
vm-support.10110/proc/4123/sessionid                                     
vm-support.10110/proc/4123/fdinfo/                                       
vm-support.10110/proc/4123/fdinfo/0                                      
vm-support.10110/proc/4123/fdinfo/2                                      
vm-support.10110/proc/4123/fdinfo/1                                      
vm-support.10110/proc/4123/loginuid                                      
vm-support.10110/proc/4123/environ                                       
vm-support.10110/proc/4123/coredump_filter                               
vm-support.10110/proc/4123/oom_score                                     
vm-support.10110/proc/4123/statm                                         
vm-support.10110/proc/4123/pagemap                                       
vm-support.10110/proc/4123/auxv                                          
vm-support.10110/proc/4123/clear_refs                                    
vm-support.10110/proc/4123/wchan                                         
vm-support.10110/proc/4123/mountinfo                                     
vm-support.10110/proc/4123/cpuset                                        
vm-support.10110/proc/4123/io                                            
vm-support.10110/proc/4123/maps                                          
vm-support.10110/proc/4123/cgroup                                        
vm-support.10110/proc/4123/oom_adj                                       
vm-support.10110/proc/4123/mountstats                                    
vm-support.10110/proc/4123/status                                        
vm-support.10110/proc/4123/schedstat                                     
vm-support.10110/proc/4123/cmdline                                       
vm-support.10110/proc/4123/latency                                       
vm-support.10110/proc/4123/limits                                        
vm-support.10110/proc/4123/net/                                          
vm-support.10110/proc/4123/net/if_inet6                                  
vm-support.10110/proc/4123/net/dev_mcast                                 
vm-support.10110/proc/4123/net/dev_snmp6/                                
vm-support.10110/proc/4123/net/dev_snmp6/eth0                            
vm-support.10110/proc/4123/net/dev_snmp6/vmnet8                          
vm-support.10110/proc/4123/net/dev_snmp6/wmaster0                        
vm-support.10110/proc/4123/net/dev_snmp6/irda0                           
vm-support.10110/proc/4123/net/dev_snmp6/wlan0                           
vm-support.10110/proc/4123/net/dev_snmp6/lo                              
vm-support.10110/proc/4123/net/dev_snmp6/vmnet1                          
vm-support.10110/proc/4123/net/netstat                                   
vm-support.10110/proc/4123/net/ip_mr_vif                                 
vm-support.10110/proc/4123/net/rt_cache                                  
vm-support.10110/proc/4123/net/route                                     
vm-support.10110/proc/4123/net/snmp                                      
vm-support.10110/proc/4123/net/igmp6                                     
vm-support.10110/proc/4123/net/mcfilter                                  
vm-support.10110/proc/4123/net/netfilter/                                
vm-support.10110/proc/4123/net/netfilter/nf_log                          
vm-support.10110/proc/4123/net/netfilter/nf_queue                        
vm-support.10110/proc/4123/net/ptype                                     
vm-support.10110/proc/4123/net/netlink                                   
vm-support.10110/proc/4123/net/ndiswrapper/                              
vm-support.10110/proc/4123/net/ndiswrapper/debug                         
vm-support.10110/proc/4123/net/softnet_stat                              
vm-support.10110/proc/4123/net/protocols                                 
vm-support.10110/proc/4123/net/igmp                                      
vm-support.10110/proc/4123/net/rt6_stats                                 
vm-support.10110/proc/4123/net/udplite6                                  
vm-support.10110/proc/4123/net/udplite                                   
vm-support.10110/proc/4123/net/tcp6                                      
vm-support.10110/proc/4123/net/sockstat6                                 
vm-support.10110/proc/4123/net/arp                                       
vm-support.10110/proc/4123/net/unix                                      
vm-support.10110/proc/4123/net/udp6                                      
vm-support.10110/proc/4123/net/tcp                                       
vm-support.10110/proc/4123/net/snmp6                                     
vm-support.10110/proc/4123/net/anycast6                                  
vm-support.10110/proc/4123/net/mcfilter6                                 
vm-support.10110/proc/4123/net/packet                                    
vm-support.10110/proc/4123/net/psched                                    
vm-support.10110/proc/4123/net/connector                                 
vm-support.10110/proc/4123/net/ip_tables_targets                         
vm-support.10110/proc/4123/net/atm/                                      
vm-support.10110/proc/4123/net/atm/pvc                                   
vm-support.10110/proc/4123/net/atm/vc                                    
vm-support.10110/proc/4123/net/atm/devices                               
vm-support.10110/proc/4123/net/atm/arp                                   
vm-support.10110/proc/4123/net/atm/svc                                   
vm-support.10110/proc/4123/net/dev                                       
vm-support.10110/proc/4123/net/raw6                                      
vm-support.10110/proc/4123/net/ip_tables_names                           
vm-support.10110/proc/4123/net/sockstat                                  
vm-support.10110/proc/4123/net/ip_tables_matches                         
vm-support.10110/proc/4123/net/udp                                       
vm-support.10110/proc/4123/net/ip6_flowlabel                             
vm-support.10110/proc/4123/net/irda/                                     
vm-support.10110/proc/4123/net/irda/irias                                
vm-support.10110/proc/4123/net/irda/irlmp                                
vm-support.10110/proc/4123/net/irda/irttp                                
vm-support.10110/proc/4123/net/irda/discovery                            
vm-support.10110/proc/4123/net/irda/irlap                                
vm-support.10110/proc/4123/net/rt_acct                                   
vm-support.10110/proc/4123/net/raw                                       
vm-support.10110/proc/4123/net/wireless                                  
vm-support.10110/proc/4123/net/ip_mr_cache                               
vm-support.10110/proc/4123/net/stat/                                     
vm-support.10110/proc/4123/net/stat/arp_cache                            
vm-support.10110/proc/4123/net/stat/rt_cache                             
vm-support.10110/proc/4123/net/stat/ndisc_cache                          
vm-support.10110/proc/4123/net/stat/clip_arp_cache                       
vm-support.10110/proc/4123/net/ipv6_route                                
vm-support.10110/proc/4123/net/tr_rif                                    
vm-support.10110/proc/4123/task/                                         
vm-support.10110/proc/4123/task/4123/                                    
vm-support.10110/proc/4123/task/4123/smaps                               
vm-support.10110/proc/4123/task/4123/attr/                               
vm-support.10110/proc/4123/task/4123/attr/prev                           
vm-support.10110/proc/4123/task/4123/attr/keycreate                      
vm-support.10110/proc/4123/task/4123/attr/exec                           
vm-support.10110/proc/4123/task/4123/attr/fscreate                       
vm-support.10110/proc/4123/task/4123/attr/sockcreate                     
vm-support.10110/proc/4123/task/4123/attr/current                        
vm-support.10110/proc/4123/task/4123/sched                               
vm-support.10110/proc/4123/task/4123/sessionid                           
vm-support.10110/proc/4123/task/4123/fdinfo/                             
vm-support.10110/proc/4123/task/4123/fdinfo/0                            
vm-support.10110/proc/4123/task/4123/fdinfo/2                            
vm-support.10110/proc/4123/task/4123/fdinfo/1                            
vm-support.10110/proc/4123/task/4123/loginuid                            
vm-support.10110/proc/4123/task/4123/environ                             
vm-support.10110/proc/4123/task/4123/oom_score                           
vm-support.10110/proc/4123/task/4123/statm                               
vm-support.10110/proc/4123/task/4123/pagemap                             
vm-support.10110/proc/4123/task/4123/auxv                                
vm-support.10110/proc/4123/task/4123/clear_refs                          
vm-support.10110/proc/4123/task/4123/wchan                               
vm-support.10110/proc/4123/task/4123/mountinfo                           
vm-support.10110/proc/4123/task/4123/cpuset                              
vm-support.10110/proc/4123/task/4123/io                                  
vm-support.10110/proc/4123/task/4123/maps                                
vm-support.10110/proc/4123/task/4123/cgroup                              
vm-support.10110/proc/4123/task/4123/oom_adj                             
vm-support.10110/proc/4123/task/4123/status                              
vm-support.10110/proc/4123/task/4123/schedstat                           
vm-support.10110/proc/4123/task/4123/cmdline                             
vm-support.10110/proc/4123/task/4123/latency                             
vm-support.10110/proc/4123/task/4123/limits                              
vm-support.10110/proc/4123/task/4123/mounts                              
vm-support.10110/proc/4123/task/4123/stat                                
vm-support.10110/proc/4123/task/4123/mem                                 
vm-support.10110/proc/4123/mounts                                        
vm-support.10110/proc/4123/stat                                          
vm-support.10110/proc/4123/mem                                           
vm-support.10110/proc/zoneinfo                                           
vm-support.10110/proc/1180/                                              
vm-support.10110/proc/1180/smaps                                         
vm-support.10110/proc/1180/attr/                                         
vm-support.10110/proc/1180/attr/prev                                     
vm-support.10110/proc/1180/attr/keycreate                                
vm-support.10110/proc/1180/attr/exec                                     
vm-support.10110/proc/1180/attr/fscreate                                 
vm-support.10110/proc/1180/attr/sockcreate                               
vm-support.10110/proc/1180/attr/current                                  
vm-support.10110/proc/1180/sched                                         
vm-support.10110/proc/1180/sessionid                                     
vm-support.10110/proc/1180/loginuid                                      
vm-support.10110/proc/1180/environ                                       
vm-support.10110/proc/1180/coredump_filter                               
vm-support.10110/proc/1180/oom_score                                     
vm-support.10110/proc/1180/statm                                         
vm-support.10110/proc/1180/pagemap                                       
vm-support.10110/proc/1180/auxv                                          
vm-support.10110/proc/1180/clear_refs                                    
vm-support.10110/proc/1180/wchan                                         
vm-support.10110/proc/1180/mountinfo                                     
vm-support.10110/proc/1180/cpuset                                        
vm-support.10110/proc/1180/io                                            
vm-support.10110/proc/1180/maps                                          
vm-support.10110/proc/1180/cgroup                                        
vm-support.10110/proc/1180/oom_adj                                       
vm-support.10110/proc/1180/mountstats                                    
vm-support.10110/proc/1180/status                                        
vm-support.10110/proc/1180/schedstat                                     
vm-support.10110/proc/1180/cmdline                                       
vm-support.10110/proc/1180/latency                                       
vm-support.10110/proc/1180/limits                                        
vm-support.10110/proc/1180/net/                                          
vm-support.10110/proc/1180/net/if_inet6                                  
vm-support.10110/proc/1180/net/dev_mcast                                 
vm-support.10110/proc/1180/net/dev_snmp6/                                
vm-support.10110/proc/1180/net/dev_snmp6/eth0                            
vm-support.10110/proc/1180/net/dev_snmp6/vmnet8                          
vm-support.10110/proc/1180/net/dev_snmp6/wmaster0                        
vm-support.10110/proc/1180/net/dev_snmp6/irda0                           
vm-support.10110/proc/1180/net/dev_snmp6/wlan0                           
vm-support.10110/proc/1180/net/dev_snmp6/lo                              
vm-support.10110/proc/1180/net/dev_snmp6/vmnet1                          
vm-support.10110/proc/1180/net/netstat                                   
vm-support.10110/proc/1180/net/ip_mr_vif                                 
vm-support.10110/proc/1180/net/rt_cache                                  
vm-support.10110/proc/1180/net/route                                     
vm-support.10110/proc/1180/net/snmp                                      
vm-support.10110/proc/1180/net/igmp6                                     
vm-support.10110/proc/1180/net/mcfilter                                  
vm-support.10110/proc/1180/net/netfilter/                                
vm-support.10110/proc/1180/net/netfilter/nf_log                          
vm-support.10110/proc/1180/net/netfilter/nf_queue                        
vm-support.10110/proc/1180/net/ptype                                     
vm-support.10110/proc/1180/net/netlink                                   
vm-support.10110/proc/1180/net/ndiswrapper/                              
vm-support.10110/proc/1180/net/ndiswrapper/debug                         
vm-support.10110/proc/1180/net/softnet_stat                              
vm-support.10110/proc/1180/net/protocols                                 
vm-support.10110/proc/1180/net/igmp                                      
vm-support.10110/proc/1180/net/rt6_stats                                 
vm-support.10110/proc/1180/net/udplite6                                  
vm-support.10110/proc/1180/net/udplite                                   
vm-support.10110/proc/1180/net/tcp6                                      
vm-support.10110/proc/1180/net/sockstat6                                 
vm-support.10110/proc/1180/net/arp                                       
vm-support.10110/proc/1180/net/unix                                      
vm-support.10110/proc/1180/net/udp6                                      
vm-support.10110/proc/1180/net/tcp                                       
vm-support.10110/proc/1180/net/snmp6                                     
vm-support.10110/proc/1180/net/anycast6                                  
vm-support.10110/proc/1180/net/mcfilter6                                 
vm-support.10110/proc/1180/net/packet                                    
vm-support.10110/proc/1180/net/psched                                    
vm-support.10110/proc/1180/net/connector                                 
vm-support.10110/proc/1180/net/ip_tables_targets                         
vm-support.10110/proc/1180/net/atm/                                      
vm-support.10110/proc/1180/net/atm/pvc                                   
vm-support.10110/proc/1180/net/atm/vc                                    
vm-support.10110/proc/1180/net/atm/devices                               
vm-support.10110/proc/1180/net/atm/arp                                   
vm-support.10110/proc/1180/net/atm/svc                                   
vm-support.10110/proc/1180/net/dev                                       
vm-support.10110/proc/1180/net/raw6                                      
vm-support.10110/proc/1180/net/ip_tables_names                           
vm-support.10110/proc/1180/net/sockstat                                  
vm-support.10110/proc/1180/net/ip_tables_matches                         
vm-support.10110/proc/1180/net/udp                                       
vm-support.10110/proc/1180/net/ip6_flowlabel                             
vm-support.10110/proc/1180/net/irda/                                     
vm-support.10110/proc/1180/net/irda/irias                                
vm-support.10110/proc/1180/net/irda/irlmp                                
vm-support.10110/proc/1180/net/irda/irttp                                
vm-support.10110/proc/1180/net/irda/discovery                            
vm-support.10110/proc/1180/net/irda/irlap                                
vm-support.10110/proc/1180/net/rt_acct                                   
vm-support.10110/proc/1180/net/raw                                       
vm-support.10110/proc/1180/net/wireless                                  
vm-support.10110/proc/1180/net/ip_mr_cache                               
vm-support.10110/proc/1180/net/stat/                                     
vm-support.10110/proc/1180/net/stat/arp_cache                            
vm-support.10110/proc/1180/net/stat/rt_cache                             
vm-support.10110/proc/1180/net/stat/ndisc_cache                          
vm-support.10110/proc/1180/net/stat/clip_arp_cache                       
vm-support.10110/proc/1180/net/ipv6_route                                
vm-support.10110/proc/1180/net/tr_rif                                    
vm-support.10110/proc/1180/task/                                         
vm-support.10110/proc/1180/task/1180/                                    
vm-support.10110/proc/1180/task/1180/smaps                               
vm-support.10110/proc/1180/task/1180/attr/                               
vm-support.10110/proc/1180/task/1180/attr/prev                           
vm-support.10110/proc/1180/task/1180/attr/keycreate                      
vm-support.10110/proc/1180/task/1180/attr/exec                           
vm-support.10110/proc/1180/task/1180/attr/fscreate                       
vm-support.10110/proc/1180/task/1180/attr/sockcreate                     
vm-support.10110/proc/1180/task/1180/attr/current                        
vm-support.10110/proc/1180/task/1180/sched                               
vm-support.10110/proc/1180/task/1180/sessionid                           
vm-support.10110/proc/1180/task/1180/loginuid                            
vm-support.10110/proc/1180/task/1180/environ                             
vm-support.10110/proc/1180/task/1180/oom_score                           
vm-support.10110/proc/1180/task/1180/statm                               
vm-support.10110/proc/1180/task/1180/pagemap                             
vm-support.10110/proc/1180/task/1180/auxv                                
vm-support.10110/proc/1180/task/1180/clear_refs                          
vm-support.10110/proc/1180/task/1180/wchan                               
vm-support.10110/proc/1180/task/1180/mountinfo                           
vm-support.10110/proc/1180/task/1180/cpuset                              
vm-support.10110/proc/1180/task/1180/io                                  
vm-support.10110/proc/1180/task/1180/maps                                
vm-support.10110/proc/1180/task/1180/cgroup                              
vm-support.10110/proc/1180/task/1180/oom_adj                             
vm-support.10110/proc/1180/task/1180/status                              
vm-support.10110/proc/1180/task/1180/schedstat                           
vm-support.10110/proc/1180/task/1180/cmdline                             
vm-support.10110/proc/1180/task/1180/latency                             
vm-support.10110/proc/1180/task/1180/limits                              
vm-support.10110/proc/1180/task/1180/mounts                              
vm-support.10110/proc/1180/task/1180/stat                                
vm-support.10110/proc/1180/task/1180/mem                                 
vm-support.10110/proc/1180/mounts                                        
vm-support.10110/proc/1180/stat                                          
vm-support.10110/proc/1180/mem                                           
vm-support.10110/proc/6699/                                              
vm-support.10110/proc/6699/smaps                                         
vm-support.10110/proc/6699/attr/                                         
vm-support.10110/proc/6699/attr/prev                                     
vm-support.10110/proc/6699/attr/keycreate                                
vm-support.10110/proc/6699/attr/exec                                     
vm-support.10110/proc/6699/attr/fscreate                                 
vm-support.10110/proc/6699/attr/sockcreate                               
vm-support.10110/proc/6699/attr/current                                  
vm-support.10110/proc/6699/sched                                         
vm-support.10110/proc/6699/sessionid                                     
vm-support.10110/proc/6699/fdinfo/                                       
vm-support.10110/proc/6699/fdinfo/3                                      
vm-support.10110/proc/6699/fdinfo/16                                     
vm-support.10110/proc/6699/fdinfo/21                                     
vm-support.10110/proc/6699/fdinfo/5                                      
vm-support.10110/proc/6699/fdinfo/8                                      
vm-support.10110/proc/6699/fdinfo/6                                      
vm-support.10110/proc/6699/fdinfo/13                                     
vm-support.10110/proc/6699/fdinfo/0                                      
vm-support.10110/proc/6699/fdinfo/9                                      
vm-support.10110/proc/6699/fdinfo/14                                     
vm-support.10110/proc/6699/fdinfo/12                                     
vm-support.10110/proc/6699/fdinfo/7                                      
vm-support.10110/proc/6699/fdinfo/17                                     
vm-support.10110/proc/6699/fdinfo/4                                      
vm-support.10110/proc/6699/fdinfo/18                                     
vm-support.10110/proc/6699/fdinfo/2                                      
vm-support.10110/proc/6699/fdinfo/11                                     
vm-support.10110/proc/6699/fdinfo/20                                     
vm-support.10110/proc/6699/fdinfo/19                                     
vm-support.10110/proc/6699/fdinfo/15                                     
vm-support.10110/proc/6699/fdinfo/1                                      
vm-support.10110/proc/6699/fdinfo/10                                     
vm-support.10110/proc/6699/loginuid                                      
vm-support.10110/proc/6699/environ                                       
vm-support.10110/proc/6699/coredump_filter                               
vm-support.10110/proc/6699/oom_score                                     
vm-support.10110/proc/6699/statm                                         
vm-support.10110/proc/6699/pagemap                                       
vm-support.10110/proc/6699/auxv                                          
vm-support.10110/proc/6699/clear_refs                                    
vm-support.10110/proc/6699/wchan                                         
vm-support.10110/proc/6699/mountinfo                                     
vm-support.10110/proc/6699/cpuset                                        
vm-support.10110/proc/6699/io                                            
vm-support.10110/proc/6699/maps                                          
vm-support.10110/proc/6699/cgroup                                        
vm-support.10110/proc/6699/oom_adj                                       
vm-support.10110/proc/6699/mountstats                                    
vm-support.10110/proc/6699/status                                        
vm-support.10110/proc/6699/schedstat                                     
vm-support.10110/proc/6699/cmdline                                       
vm-support.10110/proc/6699/latency                                       
vm-support.10110/proc/6699/limits                                        
vm-support.10110/proc/6699/net/                                          
vm-support.10110/proc/6699/net/if_inet6                                  
vm-support.10110/proc/6699/net/dev_mcast                                 
vm-support.10110/proc/6699/net/dev_snmp6/                                
vm-support.10110/proc/6699/net/dev_snmp6/eth0                            
vm-support.10110/proc/6699/net/dev_snmp6/vmnet8                          
vm-support.10110/proc/6699/net/dev_snmp6/wmaster0                        
vm-support.10110/proc/6699/net/dev_snmp6/irda0                           
vm-support.10110/proc/6699/net/dev_snmp6/wlan0                           
vm-support.10110/proc/6699/net/dev_snmp6/lo                              
vm-support.10110/proc/6699/net/dev_snmp6/vmnet1                          
vm-support.10110/proc/6699/net/netstat                                   
vm-support.10110/proc/6699/net/ip_mr_vif                                 
vm-support.10110/proc/6699/net/rt_cache                                  
vm-support.10110/proc/6699/net/route                                     
vm-support.10110/proc/6699/net/snmp                                      
vm-support.10110/proc/6699/net/igmp6                                     
vm-support.10110/proc/6699/net/mcfilter                                  
vm-support.10110/proc/6699/net/netfilter/                                
vm-support.10110/proc/6699/net/netfilter/nf_log                          
vm-support.10110/proc/6699/net/netfilter/nf_queue                        
vm-support.10110/proc/6699/net/ptype                                     
vm-support.10110/proc/6699/net/netlink                                   
vm-support.10110/proc/6699/net/ndiswrapper/                              
vm-support.10110/proc/6699/net/ndiswrapper/debug                         
vm-support.10110/proc/6699/net/softnet_stat                              
vm-support.10110/proc/6699/net/protocols                                 
vm-support.10110/proc/6699/net/igmp                                      
vm-support.10110/proc/6699/net/rt6_stats                                 
vm-support.10110/proc/6699/net/udplite6                                  
vm-support.10110/proc/6699/net/udplite                                   
vm-support.10110/proc/6699/net/tcp6                                      
vm-support.10110/proc/6699/net/sockstat6                                 
vm-support.10110/proc/6699/net/arp                                       
vm-support.10110/proc/6699/net/unix                                      
vm-support.10110/proc/6699/net/udp6                                      
vm-support.10110/proc/6699/net/tcp                                       
vm-support.10110/proc/6699/net/snmp6                                     
vm-support.10110/proc/6699/net/anycast6                                  
vm-support.10110/proc/6699/net/mcfilter6                                 
vm-support.10110/proc/6699/net/packet                                    
vm-support.10110/proc/6699/net/psched                                    
vm-support.10110/proc/6699/net/connector                                 
vm-support.10110/proc/6699/net/ip_tables_targets                         
vm-support.10110/proc/6699/net/atm/                                      
vm-support.10110/proc/6699/net/atm/pvc                                   
vm-support.10110/proc/6699/net/atm/vc                                    
vm-support.10110/proc/6699/net/atm/devices                               
vm-support.10110/proc/6699/net/atm/arp                                   
vm-support.10110/proc/6699/net/atm/svc                                   
vm-support.10110/proc/6699/net/dev                                       
vm-support.10110/proc/6699/net/raw6                                      
vm-support.10110/proc/6699/net/ip_tables_names                           
vm-support.10110/proc/6699/net/sockstat                                  
vm-support.10110/proc/6699/net/ip_tables_matches                         
vm-support.10110/proc/6699/net/udp                                       
vm-support.10110/proc/6699/net/ip6_flowlabel                             
vm-support.10110/proc/6699/net/irda/                                     
vm-support.10110/proc/6699/net/irda/irias                                
vm-support.10110/proc/6699/net/irda/irlmp                                
vm-support.10110/proc/6699/net/irda/irttp                                
vm-support.10110/proc/6699/net/irda/discovery                            
vm-support.10110/proc/6699/net/irda/irlap                                
vm-support.10110/proc/6699/net/rt_acct                                   
vm-support.10110/proc/6699/net/raw                                       
vm-support.10110/proc/6699/net/wireless                                  
vm-support.10110/proc/6699/net/ip_mr_cache                               
vm-support.10110/proc/6699/net/stat/                                     
vm-support.10110/proc/6699/net/stat/arp_cache                            
vm-support.10110/proc/6699/net/stat/rt_cache                             
vm-support.10110/proc/6699/net/stat/ndisc_cache                          
vm-support.10110/proc/6699/net/stat/clip_arp_cache                       
vm-support.10110/proc/6699/net/ipv6_route                                
vm-support.10110/proc/6699/net/tr_rif                                    
vm-support.10110/proc/6699/task/                                         
vm-support.10110/proc/6699/task/6699/                                    
vm-support.10110/proc/6699/task/6699/smaps                               
vm-support.10110/proc/6699/task/6699/attr/                               
vm-support.10110/proc/6699/task/6699/attr/prev                           
vm-support.10110/proc/6699/task/6699/attr/keycreate                      
vm-support.10110/proc/6699/task/6699/attr/exec                           
vm-support.10110/proc/6699/task/6699/attr/fscreate                       
vm-support.10110/proc/6699/task/6699/attr/sockcreate                     
vm-support.10110/proc/6699/task/6699/attr/current                        
vm-support.10110/proc/6699/task/6699/sched                               
vm-support.10110/proc/6699/task/6699/sessionid                           
vm-support.10110/proc/6699/task/6699/fdinfo/                             
vm-support.10110/proc/6699/task/6699/fdinfo/3                            
vm-support.10110/proc/6699/task/6699/fdinfo/16                           
vm-support.10110/proc/6699/task/6699/fdinfo/21                           
vm-support.10110/proc/6699/task/6699/fdinfo/5                            
vm-support.10110/proc/6699/task/6699/fdinfo/8                            
vm-support.10110/proc/6699/task/6699/fdinfo/6                            
vm-support.10110/proc/6699/task/6699/fdinfo/13                           
vm-support.10110/proc/6699/task/6699/fdinfo/0                            
vm-support.10110/proc/6699/task/6699/fdinfo/9                            
vm-support.10110/proc/6699/task/6699/fdinfo/14                           
vm-support.10110/proc/6699/task/6699/fdinfo/12                           
vm-support.10110/proc/6699/task/6699/fdinfo/7                            
vm-support.10110/proc/6699/task/6699/fdinfo/17                           
vm-support.10110/proc/6699/task/6699/fdinfo/4                            
vm-support.10110/proc/6699/task/6699/fdinfo/18                           
vm-support.10110/proc/6699/task/6699/fdinfo/2                            
vm-support.10110/proc/6699/task/6699/fdinfo/11                           
vm-support.10110/proc/6699/task/6699/fdinfo/20                           
vm-support.10110/proc/6699/task/6699/fdinfo/19                           
vm-support.10110/proc/6699/task/6699/fdinfo/15                           
vm-support.10110/proc/6699/task/6699/fdinfo/1                            
vm-support.10110/proc/6699/task/6699/fdinfo/10                           
vm-support.10110/proc/6699/task/6699/loginuid                            
vm-support.10110/proc/6699/task/6699/environ                             
vm-support.10110/proc/6699/task/6699/oom_score                           
vm-support.10110/proc/6699/task/6699/statm                               
vm-support.10110/proc/6699/task/6699/pagemap                             
vm-support.10110/proc/6699/task/6699/auxv                                
vm-support.10110/proc/6699/task/6699/clear_refs                          
vm-support.10110/proc/6699/task/6699/wchan                               
vm-support.10110/proc/6699/task/6699/mountinfo                           
vm-support.10110/proc/6699/task/6699/cpuset                              
vm-support.10110/proc/6699/task/6699/io                                  
vm-support.10110/proc/6699/task/6699/maps                                
vm-support.10110/proc/6699/task/6699/cgroup                              
vm-support.10110/proc/6699/task/6699/oom_adj                             
vm-support.10110/proc/6699/task/6699/status                              
vm-support.10110/proc/6699/task/6699/schedstat                           
vm-support.10110/proc/6699/task/6699/cmdline                             
vm-support.10110/proc/6699/task/6699/latency                             
vm-support.10110/proc/6699/task/6699/limits                              
vm-support.10110/proc/6699/task/6699/mounts                              
vm-support.10110/proc/6699/task/6699/stat                                
vm-support.10110/proc/6699/task/6699/mem                                 
vm-support.10110/proc/6699/mounts                                        
vm-support.10110/proc/6699/stat                                          
vm-support.10110/proc/6699/mem                                           
vm-support.10110/proc/cpuinfo                                            
vm-support.10110/proc/6430/                                              
vm-support.10110/proc/6430/smaps                                         
vm-support.10110/proc/6430/attr/                                         
vm-support.10110/proc/6430/attr/prev                                     
vm-support.10110/proc/6430/attr/keycreate                                
vm-support.10110/proc/6430/attr/exec                                     
vm-support.10110/proc/6430/attr/fscreate                                 
vm-support.10110/proc/6430/attr/sockcreate                               
vm-support.10110/proc/6430/attr/current                                  
vm-support.10110/proc/6430/sched                                         
vm-support.10110/proc/6430/sessionid                                     
vm-support.10110/proc/6430/fdinfo/                                       
vm-support.10110/proc/6430/fdinfo/3                                      
vm-support.10110/proc/6430/fdinfo/5                                      
vm-support.10110/proc/6430/fdinfo/8                                      
vm-support.10110/proc/6430/fdinfo/6                                      
vm-support.10110/proc/6430/fdinfo/0                                      
vm-support.10110/proc/6430/fdinfo/9                                      
vm-support.10110/proc/6430/fdinfo/7                                      
vm-support.10110/proc/6430/fdinfo/4                                      
vm-support.10110/proc/6430/fdinfo/2                                      
vm-support.10110/proc/6430/fdinfo/11                                     
vm-support.10110/proc/6430/fdinfo/1                                      
vm-support.10110/proc/6430/fdinfo/10                                     
vm-support.10110/proc/6430/loginuid                                      
vm-support.10110/proc/6430/environ                                       
vm-support.10110/proc/6430/coredump_filter                               
vm-support.10110/proc/6430/oom_score                                     
vm-support.10110/proc/6430/statm                                         
vm-support.10110/proc/6430/pagemap                                       
vm-support.10110/proc/6430/auxv                                          
vm-support.10110/proc/6430/clear_refs                                    
vm-support.10110/proc/6430/wchan                                         
vm-support.10110/proc/6430/mountinfo                                     
vm-support.10110/proc/6430/cpuset                                        
vm-support.10110/proc/6430/io                                            
vm-support.10110/proc/6430/maps                                          
vm-support.10110/proc/6430/cgroup                                        
vm-support.10110/proc/6430/oom_adj                                       
vm-support.10110/proc/6430/mountstats                                    
vm-support.10110/proc/6430/status                                        
vm-support.10110/proc/6430/schedstat                                     
vm-support.10110/proc/6430/cmdline                                       
vm-support.10110/proc/6430/latency                                       
vm-support.10110/proc/6430/limits                                        
vm-support.10110/proc/6430/net/                                          
vm-support.10110/proc/6430/net/if_inet6                                  
vm-support.10110/proc/6430/net/dev_mcast                                 
vm-support.10110/proc/6430/net/dev_snmp6/                                
vm-support.10110/proc/6430/net/dev_snmp6/eth0                            
vm-support.10110/proc/6430/net/dev_snmp6/vmnet8                          
vm-support.10110/proc/6430/net/dev_snmp6/wmaster0                        
vm-support.10110/proc/6430/net/dev_snmp6/irda0                           
vm-support.10110/proc/6430/net/dev_snmp6/wlan0                           
vm-support.10110/proc/6430/net/dev_snmp6/lo                              
vm-support.10110/proc/6430/net/dev_snmp6/vmnet1                          
vm-support.10110/proc/6430/net/netstat                                   
vm-support.10110/proc/6430/net/ip_mr_vif                                 
vm-support.10110/proc/6430/net/rt_cache                                  
vm-support.10110/proc/6430/net/route                                     
vm-support.10110/proc/6430/net/snmp                                      
vm-support.10110/proc/6430/net/igmp6                                     
vm-support.10110/proc/6430/net/mcfilter                                  
vm-support.10110/proc/6430/net/netfilter/                                
vm-support.10110/proc/6430/net/netfilter/nf_log                          
vm-support.10110/proc/6430/net/netfilter/nf_queue                        
vm-support.10110/proc/6430/net/ptype                                     
vm-support.10110/proc/6430/net/netlink                                   
vm-support.10110/proc/6430/net/ndiswrapper/                              
vm-support.10110/proc/6430/net/ndiswrapper/debug                         
vm-support.10110/proc/6430/net/softnet_stat                              
vm-support.10110/proc/6430/net/protocols                                 
vm-support.10110/proc/6430/net/igmp                                      
vm-support.10110/proc/6430/net/rt6_stats                                 
vm-support.10110/proc/6430/net/udplite6                                  
vm-support.10110/proc/6430/net/udplite                                   
vm-support.10110/proc/6430/net/tcp6                                      
vm-support.10110/proc/6430/net/sockstat6                                 
vm-support.10110/proc/6430/net/arp                                       
vm-support.10110/proc/6430/net/unix                                      
vm-support.10110/proc/6430/net/udp6                                      
vm-support.10110/proc/6430/net/tcp                                       
vm-support.10110/proc/6430/net/snmp6                                     
vm-support.10110/proc/6430/net/anycast6                                  
vm-support.10110/proc/6430/net/mcfilter6                                 
vm-support.10110/proc/6430/net/packet                                    
vm-support.10110/proc/6430/net/psched                                    
vm-support.10110/proc/6430/net/connector                                 
vm-support.10110/proc/6430/net/ip_tables_targets                         
vm-support.10110/proc/6430/net/atm/                                      
vm-support.10110/proc/6430/net/atm/pvc                                   
vm-support.10110/proc/6430/net/atm/vc                                    
vm-support.10110/proc/6430/net/atm/devices                               
vm-support.10110/proc/6430/net/atm/arp                                   
vm-support.10110/proc/6430/net/atm/svc                                   
vm-support.10110/proc/6430/net/dev                                       
vm-support.10110/proc/6430/net/raw6                                      
vm-support.10110/proc/6430/net/ip_tables_names                           
vm-support.10110/proc/6430/net/sockstat                                  
vm-support.10110/proc/6430/net/ip_tables_matches                         
vm-support.10110/proc/6430/net/udp                                       
vm-support.10110/proc/6430/net/ip6_flowlabel                             
vm-support.10110/proc/6430/net/irda/                                     
vm-support.10110/proc/6430/net/irda/irias                                
vm-support.10110/proc/6430/net/irda/irlmp                                
vm-support.10110/proc/6430/net/irda/irttp                                
vm-support.10110/proc/6430/net/irda/discovery                            
vm-support.10110/proc/6430/net/irda/irlap                                
vm-support.10110/proc/6430/net/rt_acct                                   
vm-support.10110/proc/6430/net/raw                                       
vm-support.10110/proc/6430/net/wireless                                  
vm-support.10110/proc/6430/net/ip_mr_cache                               
vm-support.10110/proc/6430/net/stat/                                     
vm-support.10110/proc/6430/net/stat/arp_cache                            
vm-support.10110/proc/6430/net/stat/rt_cache                             
vm-support.10110/proc/6430/net/stat/ndisc_cache                          
vm-support.10110/proc/6430/net/stat/clip_arp_cache                       
vm-support.10110/proc/6430/net/ipv6_route                                
vm-support.10110/proc/6430/net/tr_rif                                    
vm-support.10110/proc/6430/task/                                         
vm-support.10110/proc/6430/task/6430/                                    
vm-support.10110/proc/6430/task/6430/smaps                               
vm-support.10110/proc/6430/task/6430/attr/                               
vm-support.10110/proc/6430/task/6430/attr/prev                           
vm-support.10110/proc/6430/task/6430/attr/keycreate                      
vm-support.10110/proc/6430/task/6430/attr/exec                           
vm-support.10110/proc/6430/task/6430/attr/fscreate                       
vm-support.10110/proc/6430/task/6430/attr/sockcreate                     
vm-support.10110/proc/6430/task/6430/attr/current                        
vm-support.10110/proc/6430/task/6430/sched                               
vm-support.10110/proc/6430/task/6430/sessionid                           
vm-support.10110/proc/6430/task/6430/fdinfo/                             
vm-support.10110/proc/6430/task/6430/fdinfo/3                            
vm-support.10110/proc/6430/task/6430/fdinfo/5                            
vm-support.10110/proc/6430/task/6430/fdinfo/8                            
vm-support.10110/proc/6430/task/6430/fdinfo/6                            
vm-support.10110/proc/6430/task/6430/fdinfo/0                            
vm-support.10110/proc/6430/task/6430/fdinfo/9                            
vm-support.10110/proc/6430/task/6430/fdinfo/7                            
vm-support.10110/proc/6430/task/6430/fdinfo/4                            
vm-support.10110/proc/6430/task/6430/fdinfo/2                            
vm-support.10110/proc/6430/task/6430/fdinfo/11                           
vm-support.10110/proc/6430/task/6430/fdinfo/1                            
vm-support.10110/proc/6430/task/6430/fdinfo/10                           
vm-support.10110/proc/6430/task/6430/loginuid                            
vm-support.10110/proc/6430/task/6430/environ                             
vm-support.10110/proc/6430/task/6430/oom_score                           
vm-support.10110/proc/6430/task/6430/statm                               
vm-support.10110/proc/6430/task/6430/pagemap                             
vm-support.10110/proc/6430/task/6430/auxv                                
vm-support.10110/proc/6430/task/6430/clear_refs                          
vm-support.10110/proc/6430/task/6430/wchan                               
vm-support.10110/proc/6430/task/6430/mountinfo                           
vm-support.10110/proc/6430/task/6430/cpuset                              
vm-support.10110/proc/6430/task/6430/io                                  
vm-support.10110/proc/6430/task/6430/maps                                
vm-support.10110/proc/6430/task/6430/cgroup                              
vm-support.10110/proc/6430/task/6430/oom_adj                             
vm-support.10110/proc/6430/task/6430/status                              
vm-support.10110/proc/6430/task/6430/schedstat                           
vm-support.10110/proc/6430/task/6430/cmdline                             
vm-support.10110/proc/6430/task/6430/latency                             
vm-support.10110/proc/6430/task/6430/limits                              
vm-support.10110/proc/6430/task/6430/mounts                              
vm-support.10110/proc/6430/task/6430/stat                                
vm-support.10110/proc/6430/task/6430/mem                                 
vm-support.10110/proc/6430/mounts                                        
vm-support.10110/proc/6430/stat                                          
vm-support.10110/proc/6430/mem                                           
vm-support.10110/proc/asound/                                            
vm-support.10110/proc/asound/oss/                                        
vm-support.10110/proc/asound/oss/sndstat                                 
vm-support.10110/proc/asound/oss/devices                                 
vm-support.10110/proc/asound/version                                     
vm-support.10110/proc/asound/modules                                     
vm-support.10110/proc/asound/pcm                                         
vm-support.10110/proc/asound/devices                                     
vm-support.10110/proc/asound/timers                                      
vm-support.10110/proc/asound/seq/                                        
vm-support.10110/proc/asound/seq/oss                                     
vm-support.10110/proc/asound/seq/queues                                  
vm-support.10110/proc/asound/seq/drivers                                 
vm-support.10110/proc/asound/seq/timer                                   
vm-support.10110/proc/asound/seq/clients                                 
vm-support.10110/proc/asound/cards                                       
vm-support.10110/var/                                                    
vm-support.10110/var/lib/                                                
vm-support.10110/var/lib/vmware/                                         
vm-support.10110/var/lib/vmware/Virtual Machines/                        
vm-support.10110/var/lib/vmware/Virtual Machines/Windows Server 2003 Enterprise Edition/                                                          
vm-support.10110/var/lib/vmware/Virtual Machines/Windows Server 2003 Enterprise Edition/core                                                      
vm-support.10110/var/lib/vmware/Virtual Machines/Windows Server 2003 Enterprise Edition/vmware.log                                                
vm-support.10110/var/lib/vmware/Virtual Machines/Windows Server 2003 Enterprise Edition/vmware-0.log                                              
vm-support.10110/var/lib/vmware/Virtual Machines/Windows Server 2003 Enterprise Edition/vmware-1.log                                              
vm-support.10110/var/lib/vmware/Virtual Machines/Windows Server 2003 Enterprise Edition/vmware-2.log                                              
vm-support.10110/var/lib/vmware/Virtual Machines/Windows Server 2003 Enterprise Edition/Windows Server 2003 Enterprise Edition.vmx                
vm-support.10110/var/lib/vmware/Virtual Machines/Windows XP Professional/
vm-support.10110/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmx                                              
vm-support.10110/var/lib/vmware/Virtual Machines/Windows XP Professional/vmware.log                                                               
vm-support.10110/var/lib/vmware/Virtual Machines/Windows XP Professional/vmware-0.log                                                             
vm-support.10110/var/lib/vmware/Virtual Machines/Windows XP Professional/vmware-1.log                                                             
vm-support.10110/var/lib/vmware/Virtual Machines/Windows XP Professional/vmware-2.log                                                             
vm-support.10110/var/lib/vmware/Virtual Machines/Other Linux 2.6.x kernel/                                                                        
vm-support.10110/var/lib/vmware/Virtual Machines/Other Linux 2.6.x kernel/vmware.log                                                              
vm-support.10110/var/lib/vmware/Virtual Machines/Other Linux 2.6.x kernel/Other Linux 2.6.x kernel.vmx                                            
vm-support.10110/var/lib/vmware/Virtual Machines/Other Linux 2.6.x kernel/vmware-0.log                                                            
vm-support.10110/var/lib/vmware/Virtual Machines/Other Linux 2.6.x kernel/vmware-1.log                                                            
vm-support.10110/var/lib/vmware/Virtual Machines/Other Linux 2.6.x kernel/vmware-2.log                                                            
vm-support.10110/var/log/                                                
vm-support.10110/var/log/messages.5.gz                                   
vm-support.10110/var/log/boot                                            
vm-support.10110/var/log/vmware-mui/                                     
vm-support.10110/var/log/messages.3.gz                                   
vm-support.10110/var/log/messages                                        
vm-support.10110/var/log/bootstrap.log                                   
vm-support.10110/var/log/messages.6.gz                                   
vm-support.10110/var/log/messages.0                                      
vm-support.10110/var/log/messages.2.gz                                   
vm-support.10110/var/log/messages.4.gz                                   
vm-support.10110/var/log/vmware/                                         
vm-support.10110/var/log/vmware/vmware-serverd-2.log                     
vm-support.10110/var/log/vmware/vmware-serverd-0.log                     
vm-support.10110/var/log/vmware/vmware-serverd-4.log                     
vm-support.10110/var/log/vmware/vmware-serverd-3.log                     
vm-support.10110/var/log/vmware/vmware-serverd-7.log                     
vm-support.10110/var/log/vmware/vmware-serverd-1.log                     
vm-support.10110/var/log/vmware/vmware-serverd-5.log                     
vm-support.10110/var/log/vmware/vmware-serverd.log                       
vm-support.10110/var/log/vmware/vmware-serverd-9.log                     
vm-support.10110/var/log/vmware/vmware-serverd-8.log                     
vm-support.10110/var/log/vmware/vmware-serverd-6.log                     
vm-support.10110/var/log/messages.1.gz                                   
vm-support.10110/usr/                                                    
vm-support.10110/usr/lib/                                                
vm-support.10110/usr/lib/vmware-mui/                                     
vm-support.10110/usr/lib/vmware-mui/apache/                              
vm-support.10110/usr/lib/vmware-mui/apache/conf/                         
vm-support.10110/tmp/                                                    
vm-support.10110/tmp/df.10110.txt                                        
vm-support.10110/tmp/vmware.10110.txt                                    
vm-support.10110/tmp/ulimit-a.10110.txt                                  
vm-support.10110/tmp/modules.10110.txt                                   
vm-support.10110/tmp/ifconfig.10110.txt                                  
vm-support.10110/tmp/uptime.10110.txt                                    
vm-support.10110/tmp/umask.10110.txt                                     
vm-support.10110/tmp/vm-support-version.10110.txt                        
vm-support.10110/tmp/uname.10110.txt                                     
vm-support.10110/tmp/issue.10110.txt                                     
vm-support.10110/tmp/lspci1.10110.txt                                    
vm-support.10110/tmp/free.10110.txt                                      
vm-support.10110/tmp/lspci2.10110.txt                                    
vm-support.10110/tmp/mount.10110.txt                                     
vm-support.10110/tmp/route.10110.txt                                     
vm-support.10110/tmp/vmware-julian/                                      
vm-support.10110/tmp/vmware-julian/ui-8760.log                           
vm-support.10110/tmp/dmesg.10110.txt                                     
vm-support.10110/tmp/date.10110.txt                                      
vm-support.10110/tmp/netstat-lan.10110.txt                               
vm-support.10110/tmp/ps-auwwx.10110.txt                                  
vm-support.10110/tmp/vmware-root/                                        
vm-support.10110/tmp/vmware-root/ui-6821.log                             
vm-support.10110/etc/                                                    
vm-support.10110/etc/xinetd.d/                                           
vm-support.10110/etc/xinetd.d/vmware-authd                               
vm-support.10110/etc/cron.hourly/                                        
vm-support.10110/etc/cron.hourly/.placeholder                            
vm-support.10110/etc/services                                            
vm-support.10110/etc/modules.conf                                        
vm-support.10110/etc/security/                                           
vm-support.10110/etc/security/namespace.init                             
vm-support.10110/etc/security/namespace.conf                             
vm-support.10110/etc/security/sepermit.conf                              
vm-support.10110/etc/security/group.conf                                 
vm-support.10110/etc/security/pam_env.conf                               
vm-support.10110/etc/security/opasswd                                    
vm-support.10110/etc/security/limits.conf                                
vm-support.10110/etc/security/access.conf                                
vm-support.10110/etc/security/time.conf                                  
vm-support.10110/etc/cron.monthly/                                       
vm-support.10110/etc/cron.monthly/.placeholder                           
vm-support.10110/etc/cron.monthly/0anacron                               
vm-support.10110/etc/cron.monthly/standard                               
vm-support.10110/etc/vmware/                                             
vm-support.10110/etc/vmware/config.old.0                                 
vm-support.10110/etc/vmware/ssl/                                         
vm-support.10110/etc/vmware/ssl/rui.crt                                  
vm-support.10110/etc/vmware/ssl/rui.key                                  
vm-support.10110/etc/vmware/signing-key.pub                              
vm-support.10110/etc/vmware/license.vs.1.0-00                            
vm-support.10110/etc/vmware/vmnet8/                                      
vm-support.10110/etc/vmware/vmnet8/nat/                                  
vm-support.10110/etc/vmware/vmnet8/nat/nat.conf                          
vm-support.10110/etc/vmware/vmnet8/dhcpd/                                
vm-support.10110/etc/vmware/vmnet8/dhcpd/dhcpd.leases                    
vm-support.10110/etc/vmware/vmnet8/dhcpd/dhcpd.leases~                   
vm-support.10110/etc/vmware/vmnet8/dhcpd/dhcpd.conf                      
vm-support.10110/etc/vmware/pam.d/                                       
vm-support.10110/etc/vmware/pam.d/vmware-authd                           
vm-support.10110/etc/vmware/vm-list                                      
vm-support.10110/etc/vmware/vm-list-private                              
vm-support.10110/etc/vmware/netmap.conf                                  
vm-support.10110/etc/vmware/config                                       
vm-support.10110/etc/vmware/installer.sh                                 
vm-support.10110/etc/vmware/vmnet1/                                      
vm-support.10110/etc/vmware/vmnet1/dhcpd/                                
vm-support.10110/etc/vmware/vmnet1/dhcpd/dhcpd.leases                    
vm-support.10110/etc/vmware/vmnet1/dhcpd/dhcpd.leases~                   
vm-support.10110/etc/vmware/vmnet1/dhcpd/dhcpd.conf                      
vm-support.10110/etc/vmware/locations                                    
vm-support.10110/etc/cron.daily/                                         
vm-support.10110/etc/cron.daily/.placeholder                             
vm-support.10110/etc/cron.daily/apt                                      
vm-support.10110/etc/cron.daily/man-db                                   
vm-support.10110/etc/cron.daily/aptitude                                 
vm-support.10110/etc/cron.daily/sysklogd                                 
vm-support.10110/etc/cron.daily/logrotate                                
vm-support.10110/etc/cron.daily/apache2                                  
vm-support.10110/etc/cron.daily/apport                                   
vm-support.10110/etc/cron.daily/find                                     
vm-support.10110/etc/cron.daily/samba                                    
vm-support.10110/etc/cron.daily/mlocate                                  
vm-support.10110/etc/cron.daily/ntp                                      
vm-support.10110/etc/cron.daily/find.notslocate.dpkg-new                 
vm-support.10110/etc/cron.daily/0anacron                                 
vm-support.10110/etc/cron.daily/standard                                 
vm-support.10110/etc/cron.daily/bsdmainutils                             
vm-support.10110/etc/cron.weekly/                                        
vm-support.10110/etc/cron.weekly/.placeholder                            
vm-support.10110/etc/cron.weekly/man-db
vm-support.10110/etc/cron.weekly/sysklogd
vm-support.10110/etc/cron.weekly/popularity-contest
vm-support.10110/etc/cron.weekly/cvs
vm-support.10110/etc/cron.weekly/0anacron
vm-support.10110/etc/cron.weekly/apt-xapian-index
vm-support.10110/etc/crontab

File: /home/julian/vm-2009-04-17.10110.tgz
NOTE: vm-2009-04-17.10110.tgz is greater than 10 MB.
Please do not attach this file when submitting an incident report.
Please contact VMware support for an ftp site.
To file a support incident, go to http://www.vmware.com/support/sr/sr_login.jsp
```

I will log a call and let you know the result, thanks again.

---

