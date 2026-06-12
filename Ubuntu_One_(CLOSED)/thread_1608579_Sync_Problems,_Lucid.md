---
title: "Sync Problems, Lucid"
date: 2010-10-29
forum: Ubuntu One (CLOSED)
---

### Post by don762003 on 2010-10-29
Ubuntu one has no problem syncing small files (I was able to sync 29 bytes) but when I try to sync anything bigger in the mb range it uploads then after it finishes it starts all over again and nothing is ever uploaded or shows up on the ubuntu one website. here is some output-

don@don-desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_CONTENT

don@don-desktop:~$ u1sdtool --current-transfers
Current uploads:
  path: /home/don/Ubuntu One/MOV005.MOD.tar.bz2
    deflated size: 8590760
    bytes written: 6197420
Current downloads: 0
don@don-desktop:~$ file:u1sdtool --current-transfers
file:u1sdtool: command not found
don@don-desktop:~$ u1sdtool --current-transfers
Current uploads:
  path: /home/don/Ubuntu One/MOV005.MOD.tar.bz2
    deflated size: 8590760
    bytes written: 7110724
Current downloads: 0
don@don-desktop:~$ u1sdtool --current-transfers
Current uploads:
  path: /home/don/Ubuntu One/MOV005.MOD.tar.bz2
    deflated size: 8590760
    bytes written: 8590760
Current downloads: 0
don@don-desktop:~$ u1sdtool --current-transfers
Current uploads:
  path: /home/don/Ubuntu One/MOV005.MOD.tar.bz2
    deflated size: 8590760
    bytes written: 8590760
Current downloads: 0
don@don-desktop:~$ u1sdtool --current-transfers
Current uploads:
  path: /home/don/Ubuntu One/MOV005.MOD.tar.bz2
    deflated size: 8590760
    bytes written: 848068
Current downloads: 0
don@don-desktop:~$

---

