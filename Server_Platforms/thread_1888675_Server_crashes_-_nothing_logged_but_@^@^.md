---
title: "Server crashes - nothing logged but @^@^"
date: 2011-11-29
forum: Server Platforms
---

### Post by harty83 on 2011-11-29
So this is the second time my server has crashed.  It just locks up.  Memory is plenty and rarely over 50% use, swap is rarely used and CPU usage minimal.  

This is hosted via Linode.  I just all of a sudden can't access the server (which hosts websites).  I try to ssh but can't communicate so I force a reboot via Linode's manager.  When I look in the logs, I can't find any reason for the lock up.  In all the logs around the time the lock up happens, I have a bunch of @^@^@^@^@^@^@^@^. 

Any ideas on the reason?

If not, any ideas on what I can setup to help debug if it happens again?

Thanks,
Alan

---

### Post by rsvancara on 2011-11-29
Use the Linode console and see what is happening.  Do you see any error messages?  

Also, I manage several Linode instances and I have not seen any crash like you are describing.  What are your running on this linode?

Randall
[http://www.knowyourlinux.com/]("http://www.knowyourlinux.com/content/backing-dvd-using-handbrake-linux")

---

### Post by arrrghhh on 2011-11-29
Doesn't linnode provide some hardware troubleshooting?  I'm wondering if you have a bad stick of RAM or something...

I would also be curious what you're running on the server, especially before it crashes.

---

### Post by harty83 on 2011-11-29
Its a web setup which was presetup by Virtualmin so the works.  Apache, mysql, bind9, postfix, proftpd, dovecot, spamassassin.  I disabled clamav as it was too resource hungry.  

Ubuntu 10.04 LTS.

I did view the web console and it was locked up as well.  Looked like it had some kind of dump but I couldn't view anything other than what was already on the screen.  Unfortunately, I closed the window before copying over any of the output. :-/.  And I've been unable to recover it via the logs.

I'm not familiar with any hardware troubleshooting for Linode.

Thanks,
Alan

---

### Post by arrrghhh on 2011-11-29
> **harty83 said:**
> I'm not familiar with any hardware troubleshooting for Linode.

I would reach out to them at the very least, to see what they have to offer.  I'm sure they would troubleshoot the RAM with a memtest at the very least, although this will obviously take your site down.  If it unearths a hardware issue, well worth it IMHO.

---

### Post by harty83 on 2011-11-30
Happened again.  This time I captured what was in the online console:
> Pid: 4587, comm: apache2 Not tainted 2.6.39.1-linode34 #1                                           
EIP: 0061:[<c01a9506>] EFLAGS: 00010246 CPU: 0                                                      
EIP is at swap_count_continued+0x176/0x180                                                          
EAX: f57bac57 EBX: eca29880 ECX: f57ba000 EDX: 00000000                                             
ESI: ed3d7ba0 EDI: 00000080 EBP: 00000c57 ESP: dd6dfe3c                                             
 DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0069                                                       
Process apache2 (pid: 4587, ti=dd6de000 task=dd4e2440 task.ti=dd6de000)                             
Stack:                                                                                              
 eb4ebc40 00005c57 00000040 00000000 c01a9601 00005c57 ed36e9c0 00000000                            
 00000000 c01a9868 e6669e60 c019b1aa 00000000 80000006 00000006 ec79520c                            
 ed343f00 b538a66e e66b8068 00000000 00000000 c3f4b025 c672b348 b980d478                            
Call Trace:                                                                                         
 [<c01a9601>] ? swap_entry_free+0xf1/0x120                                                          
 [<c01a9868>] ? swap_free+0x18/0x30                                                                 
 [<c019b1aa>] ? do_swap_page+0x2ca/0x5f0                                                            
 [<c019b70c>] ? handle_pte_fault+0x23c/0x2f0                                                        
 [<c019bcd4>] ? handle_mm_fault+0xf4/0x1b0                                                          
 [<c011f23b>] ? do_page_fault+0xfb/0x3e0                                                            
 [<c068fb50>] ? _raw_spin_lock_irq+0x10/0x20                                                        
 [<c0140c47>] ? sys_rt_sigaction+0x77/0xa0                                                          
 [<c01b0c6d>] ? filp_close+0x4d/0x80                                                                
 [<c01b0d0e>] ? sys_close+0x6e/0xc0                                                                 
 [<c011f140>] ? mm_fault_error+0xe0/0xe0                                                            
 [<c06903c6>] ? error_code+0x5a/0x60                                                                
 [<c0680000>] ? sctp_rcv_ootb+0x50/0xf0                                                             
 [<c011f140>] ? mm_fault_error+0xe0/0xe0                                                            
Code: ff 89 d8 e8 cd a2 f7 ff 01 e8 8d 76 00 c6 00 00 ba 01 00 00 00 eb b2 89 f8 3c 80 0f 94 c0 e9 b
9 fe ff ff 0f 0b eb fe 0f 0b eb fe <0f> 0b eb fe 0f 0b eb fe 66 90 83 ec 10 89 1c 24 89 c3 89 74 24 
EIP: [<c01a9506>] swap_count_continued+0x176/0x180 SS:ESP 0069:dd6dfe3c                             
---[ end trace a586823c682eb649 ]---                                                                
note: apache2[4587] exited with preempt_count 1                                                     
                                                 

Any further thoughts?

Thanks,
Alan

---

### Post by harty83 on 2011-11-30
Posted to Linode and they say its a bug in their kernel.  They gave me directions to select their updated kernel so we'll see how that goes.

---

### Post by arrrghhh on 2011-11-30
> **harty83 said:**
> Posted to Linode and they say its a bug in their kernel.  They gave me directions to select their updated kernel so we'll see how that goes.

Interesting.  I was going to note all the messages about swapping, are you overrunning your RAM...?

Hopefully the kernel update does it.  Let us know!!

---

### Post by harty83 on 2011-11-30
Not normally.  I've watched the server's resources via htop during the site's most heavy traffic and it never goes above 50% of the RAM (2048mb) and never swaps.  Some process must be kicking in that is maxing out memory in a very, very short period of time.  I haven't been able to figure out what though due to the server locking up whenever it seemed to happen (and I can't stay in front of my PC 24/7 :-)).  Maybe with the kernel fix which will hopefully keep the server from crashing, I'll be able to at least get into the server to see what the culprit is.

Thanks!
Alan

---

