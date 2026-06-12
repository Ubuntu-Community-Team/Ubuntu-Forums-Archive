---
title: "New Server partitioning &amp; setup help"
date: 2006-03-09
forum: Server Platforms
---

### Post by soccermonkey on 2006-03-09
i have 4 hard drives

1 40GB
3 200GB

system spec is 1 GHz amd processor and 1GB of ram

i need to run an apache server (vitural hosting 2-3 websites), mysql, mail, ftp, and samba.

i was thinking of doing raid 5 on the 3 200GB for samba file sharing...what type of filesystem would be good to use?  i will be sharing mp3s, video, storage, etc.

how should I partition the 40GB.  I have read that you should have a separate /, /swap, and /home.  I have also seen cases for separate /usr, /var, /var/mail, and /tmp.

i would like to hear people's input...thanks!

---

### Post by ttallos on 2006-03-10
This is what I have run with good success
/dev/mdX        RAID#     File        Size      Boot       Partition        Type
0                       1      /boot      49.3        x               1        primary
1                       1      swap     518.2MB                     2        primary
2                       5      /             rest                        3         primary


Hope this helps!

---

### Post by ttallos on 2006-03-10
ooops my table was ruined after I pressed enter...
If you want me to repost just reply.

---

### Post by ixus_123 on 2006-03-11
I don't know anything about RAID but for an example, this is my setup for my own LAMP server

mini-itx n10000 with 512mb ram & 160gb HD

hda1 = 10gb  -  /
hda5 = 2gb   -  swap
hda6 = 130gb - /var
hda7 = 2gb  -  swap
hda8 = 6gb  -  /home
hda9 = remaining space  - swap

I've been a bit generous with my partitions becuase the drive is huge for my needs so I could afford to be.

One thing that might jump out at people is how much swap I have.  This is overkill for sure!  I figured though that there is truth in the old adage that you can never have too much ram & since I didn't want to spend any more I just added extra swap & dotted it around the hard drive to hopefully speed up it's access (although I haven't set any swap priorities)

/ is overkill for me needs too - <5gb should be fine

/var - I read that var should be quite large on a server becuase spools & logs can fill it up quite fast if things go wrong.  Also, my /www is inside var so I need space for my pictures & content

You may want to have a separate for /www altogether.  Some people relocate /www to their home folder

/home - this is overkill too.  Currently I haev nothing in /home.  I made a separate home partition incase I needed to download debs or anyhting else for installing.  I had loads of space to spare so I made it 6gb just incase I need to use the server for desktop needs - ie if my main PC fails for whatever reason.

---

