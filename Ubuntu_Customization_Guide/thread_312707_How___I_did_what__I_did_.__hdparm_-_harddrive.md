---
title: "How   I did what  I did .  hdparm - harddrive"
date: 2006-12-04
forum: Ubuntu Customization Guide
---

### Post by wesley_of_course on 2006-12-04
8) 

 Not sure where to post this but here goes ;
        
                              Would this command , sudo hdparm -d1 -k1 /dev/hdb   ,   work for the harddrive in question ? (hdb )                    [http://linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1](http://linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1)   
                              [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)
                              Before ; 
                                                 wesley@Ratdog:~$ sudo hdparm -tT /dev/hdb
                                               /dev/hdb:
                                                              Timing cached reads:   880 MB in  2.00 seconds = 439.09 MB/sec
                                                              Timing buffered disk reads:   76 MB in  3.08 seconds =  24.67 MB/sec
                                       
                                                 wesley@Ratdog:~$ sudo hdparm /dev/hdb

                                                              /dev/hdb:
                                                              multcount    =  0 (off)
                                                              IO_support   =  0 (default 16-bit)
                                                             unmaskirq    =  0 (off)
                                                             using_dma    =  1 (on)
                                                             keepsettings =  0 (off)
                                                             readonly     =  0 (off)
                                                             readahead    = 256 (on)
                                                            geometry     = 24792/255/63, sectors = 398297088, start = 0

                                                    wesley@Ratdog:~$ sudo hdparm -c3 -m16 /dev/hdb
                                                            /dev/hdb:
                                                                          setting 32-bit IO_support flag to 3
                                                                          setting multcount to 16
                                                                          multcount    = 16 (on)
                                                                          IO_support   =  3 (32-bit w/sync)
                                                     
                                                     wesley@Ratdog:~$ sudo hdparm -tT /dev/hdb

                                                         /dev/hdb:
                                                                        Timing cached reads:   888 MB in  2.00 seconds = 443.97 MB/sec
                                                                        Timing buffered disk reads:   76 MB in  3.07 seconds =  24.74 MB/sec
 
                                                     wesley@Ratdog:~$ sudo hdparm -X34 -d1 -u1 /dev/hdb

                                                         /dev/hdb:
                                                                        setting unmaskirq to 1 (on)
                                                                        setting using_dma to 1 (on)
                                                                        setting xfermode to 34 (multiword DMA mode2)
                                                                        unmaskirq    =  1 (on)
                                                                        using_dma    =  1 (on)

 
                                                                 wesley@Ratdog:~$ sudo hdparm -X34 -d1 -u1 -m16 -c3 /dev/hdb

                                                         /dev/hdb:
                                                                         setting 32-bit IO_support flag to 3
                                                                         setting multcount to 16
                                                                         setting unmaskirq to 1 (on)
                                                                         setting using_dma to 1 (on)
                                                                         setting xfermode to 34 (multiword DMA mode2)
                                                                         multcount    = 16 (on)
                                                                         IO_support   =  3 (32-bit w/sync)
                                                                        unmaskirq    =  1 (on)
                                                                        using_dma    =  1 (on)
         
                              And if so , what IF I was to put it all together like this ;
                          wesley@Ratdog:~$ sudo hdparm -X34 -d1 -u1 -m16 -c3 -d1 -k1  /dev/hdb     
                          
                                                       /dev/hdb:
                                                                         setting 32-bit IO_support flag to 3
                                                                         setting multcount to 16
                                                                         setting unmaskirq to 1 (on)
                                                                         setting using_dma to 1 (on)
                                                                         setting keep_settings to 1 (on)
                                                                         setting xfermode to 34 (multiword DMA mode2)
                                                                         multcount    = 16 (on)
                                                                         IO_support   =  3 (32-bit w/sync)
                                                                         unmaskirq    =  1 (on)
                                                                         using_dma    =  1 (on)
                                                                         keepsettings =  1 (on)
                                Hope this helps and remember   I'm a newbie at this .
                                I did a lot of surf'in .
  Could someone check or reply thats in the know ?  Thanks !

---

### Post by esaym on 2006-12-05
multicount is deprecated and IO_support is for pci cards only.  Once dma is enabled it will use the fastest speed available so why are you forcing multiword mode2?

[http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance)

You can get better write performance with write caching (-W1) but it comes at a cost some say.  Do a google search for- [hdparm write caching "-W1" corruption]("http://www.google.com/search?hl=en&q=hdparm+write+caching+%22-W1%22+corruption&btnG=Google+Search") and validate for yourself whether or not you want to use it.  I use it on my ext2 filesystem with no problems.

---

### Post by wesley_of_course on 2006-12-11
Esaym , first I apologize for taking so long to reply , installed Xfce and have since 

    re-did what I did !  Still a Newb and didn't research enough .

    Read some and came up with the following ;

wesley@Ratdog:~$ sudo hdparm -qm8 -qu1 -qc1 -qd1 -d1 -k1 /dev/hdb

  wesley@Ratdog:~$ sudo hdparm /dev/hdb

/dev/hdb:
 multcount    =  8 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  1 (on)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24792/255/63, sectors = 398297088, start = 0

wesley@Ratdog:~$ sudo hdparm -tT /dev/hdb

/dev/hdb:
 Timing cached reads:   940 MB in  2.01 seconds = 468.39 MB/sec
 Timing buffered disk reads:  178 MB in  3.03 seconds =  58.84 MB/sec

wesley@Ratdog:~$ sudo hdparm -tT /dev/hdb

/dev/hdb:
 Timing cached reads:   892 MB in  2.00 seconds = 445.32 MB/sec
 Timing buffered disk reads:  178 MB in  3.03 seconds =  58.79 MB/sec
wesley@Ratdog:~$ sudo hdparm -tT /dev/hdb

/dev/hdb:
 Timing cached reads:   896 MB in  2.00 seconds = 447.33 MB/sec
 Timing buffered disk reads:  178 MB in  3.01 seconds =  59.22 MB/sec


  Would this work better ? I sure can't afford to trash anything !Thrash ,maybe .

      I do have a question tho. If I would of performed hdparm on /dev/hda from a Linux 
would it / could it set parameters for /dev/hda ?

  Thanks for the time and explanation , links , question. :oops:

---

