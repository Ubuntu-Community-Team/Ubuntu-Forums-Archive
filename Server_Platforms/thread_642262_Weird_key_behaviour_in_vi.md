---
title: "Weird key behaviour in vi"
date: 2007-12-16
forum: Server Platforms
---

### Post by Ooder on 2007-12-16
Hello,

I recently installed Ubuntu Server 7.10.  After I installed Samba, I went to edit the smb.conf file in vi.  However, I am having weird key behavior while in vi (editing mode).  The backspace key acts like the left arrow, the delete key doesn't seem to work, and other weird events while typing in vi.

Is there a problem with the keyboard setup?  I have no problems when not in vi (command line).  Any help would be appreciated, but use small words, I'm still a Linux noobie :)

---

### Post by Ooder on 2007-12-16
Update:

I tried using vim instead of vi, and the problem has disappeared.  Earlier I had installed version 6.06 and had no problems with using vi.  Anyone care to shed some light on why?  Or the difference between vim and vi?

---

### Post by Whiffle on 2007-12-16
Actually, thats normal.   Its Vi, which uses a different keyboard layout.  You can run 'vimtutor' if you want to learn to use it, or just use nano instead.

---

### Post by rsw686 on 2007-12-16
Use vim over vi. I recommend installing vim-full as it has syntax highlighting. You will need to edit vimrc to enable it with syntax on

---

