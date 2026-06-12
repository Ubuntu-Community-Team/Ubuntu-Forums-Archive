---
title: "Cant resize ubuntu partition..."
date: 2005-08-27
forum: The Cafe
---

### Post by xequence on 2005-08-27
I realised I gave ubuntu more space then it needed (16 GB vs windows' 3 GB) and I wanted to resize the partition. It is ext3... I went into the ubuntu installer and went until the partition part. I tried to resize it but clicking on the resize part gave me a red screen that said it could not resize the partition. It said "Because of an unknown reason it is imposible to resize this partition".

I want to give each OS half and half... I decided to use XP pro for all my music stuff such as Limewire, Bittorent, iTunes (not the store, the player, and after I finally get the stupid driver to work... They only have windows 2000 drivers on my computer makers site! The win 2000 ethernet and video drivers worked... Just whenever I start up my computer in windows I have a random chance of accually getting in to it or getting a blue screen with text for half a second then restarting...), and transfering the stuff to my mp3 player as sony only works on windows.

Thanks :)

EDIT: Oh, and I cant use gparted in ubuntu as it says the drive is mounted, which it is, how else can I get into ubuntu? :P Also the Qparted in the mepis live cd doesent show an option to resize it, but it does for the windows partition...

---

### Post by Wolki on 2005-08-27
I have a similar problem, have one big partition with Ubuntu and a smaller one for swap. Can't resize the big one for some reason, ideas would be appreciated.

That said, I think this question should be asked in one of the support forums instead of Community Chat. Sure, more people will see it here; but if everyone did that this forum would be completely unreadable. Not that I'm a moderator, just my humble opinion.

---

### Post by arnieboy on 2005-08-28
[QUOTE=xequence]I realised I gave ubuntu more space then it needed (16 GB vs windows' 3 GB) and I wanted to resize the partition. It is ext3... I went into the ubuntu installer and went until the partition part. I tried to resize it but clicking on the resize part gave me a red screen that said it could not resize the partition. It said "Because of an unknown reason it is imposible to resize this partition".

I want to give each OS half and half... I decided to use XP pro for all my music stuff such as Limewire, Bittorent, iTunes (not the store, the player, and after I finally get the stupid driver to work... They only have windows 2000 drivers on my computer makers site! The win 2000 ethernet and video drivers worked... Just whenever I start up my computer in windows I have a random chance of accually getting in to it or getting a blue screen with text for half a second then restarting...), and transfering the stuff to my mp3 player as sony only works on windows.

Thanks :)

EDIT: Oh, and I cant use gparted in ubuntu as it says the drive is mounted, which it is, how else can I get into ubuntu? :P Also the Qparted in the mepis live cd doesent show an option to resize it, but it does for the windows partition...[/QUOTE]
try the qtparted app on KNOPPIX. works just fine. if u cant resize the ext3 partition directly try converting it into a ext2 partition since ext3 is just ext2 + a journal.

Assuming you have a *cleanly unmounted* ext3 partition (run fsck -f on it to be sure); you can safely:

1) erase the journal (i.e. convert to ext2)
tune2fs -o ^has_journal <your partition>


2) resize it as an ext2 partition

3) recreate the journal
tunes2fs -j <your partition>

---

### Post by xequence on 2005-08-29
[QUOTE=arnieboy]try the qtparted app on KNOPPIX. works just fine. if u cant resize the ext3 partition directly try converting it into a ext2 partition since ext3 is just ext2 + a journal.

Assuming you have a *cleanly unmounted* ext3 partition (run fsck -f on it to be sure); you can safely:

1) erase the journal (i.e. convert to ext2)
tune2fs -o ^has_journal <your partition>


2) resize it as an ext2 partition

3) recreate the journal
tunes2fs -j <your partition>[/QUOTE]


WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.
WHat does the journal do?

---

### Post by arnieboy on 2005-08-29
[QUOTE=xequence]WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.
WHat does the journal do?[/QUOTE]
Journaling results in massively reduced time spent recovering a filesystem after a crash, and is therefore in high demand in environments where high availability is important, not only to improve recovery times on single machines but also to allow a crashed machine's filesystem to be recovered on another machine when we have a cluster of nodes with a shared disk. 
MAKE SURE U HAVE UNMOUNTED the root partition before u try resizing it.

---

