---
title: "[SOLVED] Ubuntu 8.04 hangs when transfering files to samba share"
date: 2008-08-19
forum: Server Platforms
---

### Post by crazy1902 on 2008-08-19
Hi guys. I am brand new to Linux. I want to create a home media file server.

I installed Ubuntu 8.04 server edition with Samba.
After a week or so of tinkering I figured out the basic commands then created ext3 filesystem on a raid5 array hosted by a 3ware 9650se raid card.

The array is slightly over 2tb but I made a gpt label on the drive with parted and created the partition no problem.

I copied a lot of files onto the array when the linux box suddenly started hanging. This is what shows on the screen and I have to unplug the power to be able to restart the computer. After restart everything seems normal but as soon as I start copying files from my windows machines to the linux share it hangs again.

Here is the screenshot and the text of the screen showing once system hung:


[72767.880279] Call Trace:
[72767.880305] [<ffffffff80285a74>] add_to_page_cache_lru+0x24/0x40
[72767.880327] [<ffffffff80285b0e>] __grab_cache_page+0x7e/0xa0
[72767.880354] [<ffffffff881eadab>] :ext3ext3_write_beg in+0x6b/0x1c0
[72767.880379] [<ffffffff802da69e>] __getblk+0x1e/0x250
[72767.880399] [<ffffffff80286a09>] generic_file_buffered_write+0x149/0x6b0
[72767.880432] [<ffffffff881f116d>] :ext3:__ext3_journal_stop +0x2d/0x60
[72767.880455] [<ffffffff802871bf>] __generic_file_aio_write_nolock+0x24f/0x400
[72767.880481] [<ffffffff802873d4>] generic_file_aio_write+0x64/0xd0
[72767.880507] [<ffffffff881e6653>] :ext3:ext3_file_write+0x23/0xc0
[72767.880527] [<ffffffff802b4c49>] do_sync_write+0xd9/0x120
[72767.880551] [<ffffffff80254260>] autoremove_wake_function+0x0/0x30
[72767.880575] [<ffffffff802c6c74>] fcntl_setlk+0x54/0x2d0
[72767.880596] [<ffffffff802b558d>] vfs_write+0xed/0x190
[72767.889615] [<ffffffff802b5df4>] sys_pwrite64+0x84/0xa0
[72767.880637] [<ffffffff8020c37e>] system_call+0x7e/0x83
[72767.889658]
[72767.880670]
[72767.880671] Code: 42 08 48 8b 07 48 89 4c c7 10 48 83 c0 01 03 f8 0e 48 89 07
[72767.880728] RIP [<ffffffff8028f39c>] lru_cache_add+0x2c/0x50
[72767.880748] RSP <ffff81007cde7ad0>
[72767.880763] CR2: ffffffffffffff8b
[72767.881023] --- [ end trace e5367919a8d79091 ]---

---

### Post by crazy1902 on 2008-08-23
Nobody knows what this type of error message means or suggest or anything?

---

### Post by Krupski on 2008-08-25
> **crazy1902 said:**
> Nobody knows what this type of error message means or suggest or anything?

I don't recognize the exact addresses and processes, but I *did* get a crash just like that on one of my servers due to BAD RAM.

I had 8GB in a server and I had two 512MB sticks lying around, so I thought "what the heck" and put them in.

The server would boot and run, but try to access a RAID drive and bang... crash with a screen that looked just like yours.

I pulled out the two 512 sticks and the machine became stable.

I tossed the ram in the garbage... :)

By the way, if you are overclocking your CPU and/or RAM, try either setting the memory voltage higher by 0.1 to 0.2 volts... or better yet stop overclocking and run your hardware at spec.

Good luck!

-- Roger

---

### Post by crazy1902 on 2008-08-25
Thank you very much for the suggestion. I am not overclocking. Trying to run as low power as possible on a Intel Celeron 430 Conroe-L 1.8GHz.

My memory is OCZ Platinum Revision 2 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 and while I am not overclocking I think it is possible that I am not giving it enough juice.

Thank you for this great hint and I will post back if it works or not.

---

### Post by Krupski on 2008-08-25
> **crazy1902 said:**
> Thank you very much for the suggestion. I am not overclocking. Trying to run as low power as possible on a Intel Celeron 430 Conroe-L 1.8GHz.

My memory is OCZ Platinum Revision 2 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 and while I am not overclocking I think it is possible that I am not giving it enough juice.

Thank you for this great hint and I will post back if it works or not.

The JEDEC standard for DDR-2 memory specifies a voltage of 1.80 volts DC.

As you know, overclockers bump this up to 2.0 or 2.2 volts to get faster timings.

A common "problem" with *Intel* motherboards is that they strictly adhere to specifications (i.e. they do not allow overclocking or overvolting).

As a result, some memory that is 2.0 or 2.2 volt simply doesn't work in an Intel board (which causes people to wrongly blame the mobo).

The memory you mentioned is rated to run from 1.9 to 2.1 volts (with built in protection from overvolting).

*IF* you are running an Intel motherboard, it MIGHT be acting flaky due to the fixed 1.8 volt memory supply.

I run Intel boards exclusively... and I have to particularly seek out 1.8 volt memory (I buy from Crucial). Other memory either won't work or - worse - run but be unreliable.

Good luck!

-- Roger

---

### Post by crazy1902 on 2008-08-25
My MB is MSI 945GCM5-F LGA 775 Intel 945GC Micro ATX.
I just set the ram voltage to 2.1 up from 1.9
This memory requires more voltage from my experience but I assumed 1.9 would be enough since the board limits it to 667 MHz. I guess I will soon find out if the increased voltage helps with stability.



Once I get this RAID to run stable I still have problem with this mad expensive 3ware controller read/writing at 20MB/s (raid 5 and raid 6) while with mdadm software raid I could get easily 100MB/s read write for a raid 5 or raid 6.
Starting to think 3ware hardware raid is not worth it because of all these problems and performance disappointment on top of it.

---

### Post by crazy1902 on 2008-09-07
Thanks a lot Krupski! I have no more problems after increasing the RAM voltage.

Thank you very much again. I also had to disable NCQ on the controller to not receive errors anymore.

---

### Post by Krupski on 2008-09-08
> **crazy1902 said:**
> Thanks a lot Krupski! I have no more problems after increasing the RAM voltage.

Thank you very much again. I also had to disable NCQ on the controller to not receive errors anymore.

Glad to hear it's working for you.

I'm confused as to why you have to disable NCQ though... are your drives supposed to support it?

Maybe it's a conflict between Linux and the controller... since the Linux disk driver itself supports NCQ?

Whatever... glad you're up and running!

---

### Post by crazy1902 on 2008-09-11
I am not sure what is going on with NCQ. My drives and my controller support it. But sometimes they will report errors without degrading the array. Now it is running rock stable.

BTW I have given up sadly on Ubuntu. It simply became too time consuming to make anything happen on that thing. Maybe I will reinstall the desktop version but will see. I just finally gave up after trying to configure ftp server which was supposed to be easy as pie but did not work to my satisfaction.

Windows will also be able to share movies directly to my media center extenders such a Dlink DSM-520.

But I have learned a lot about Linux but just do not have the time to fool around with it anymore and need things to just work without reading up for hours and days. Brought me back to MS-DOS days with the command line :-).

In any case it did the job well from what I asked of it but required me to research too much. Will maybe use it again later since I have it setup now as dual boot option.

Thanks again.

---

