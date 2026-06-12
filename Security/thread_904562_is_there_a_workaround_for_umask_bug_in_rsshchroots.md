---
title: "is there a workaround for umask bug in rssh/chroot/sftp/scp ??"
date: 2008-08-29
forum: Security
---

### Post by itobenon on 2008-08-29
I've seen bug submission reports dating back to 2007 - I'm very surprised that the bug itself hasn't been addressed - but further surprised that after searching now for DAYS, I can't even find a functioning work-around!!???

The bug is simply this - sftp IGNORES the specified umask value in rssh.conf (I assume scp does also - but haven't tested it).

I have found NO WAY go get around this!!!

I want my sftp users to have a umask of 007, and no matter what I do, they get a umask of 037.

I have seen numerous posts that refer to using a shell "wrapper" around sftp-server. This solution does NOT WORK! I get a "user executed illegal command" type of error in the log. I suspect I'm getting this error because a script file would probably want bash to execute, and I WILL NOT put bash in my chroot jail. My chroot users get ONLY SFTP - that's it.

There MUST be a suitable solution/workaround that doesn't compromise security... Does anyone have a clue what that might be???

TIA
:confused: / :mad:

---

### Post by hyper_ch on 2008-08-29
you might want to have a look at mysecureshell

---

### Post by itobenon on 2008-08-29
I MIGHT want to look @ mysecureshell ???

not only does this address my mode/umask problems, but...
LOL - holy crap!
I've spent DAYS trying to do a "virtual chroot" using chroot - which is impossible.

I have only 2 compaints about MSS:
1) I was loath to even try a package in which the programmer uses capital letters in the command. Except for the fact that it does do exactly what I want - I would refuse to use it in principle for the use of Caps .... needless to say, I've renamed the command to a proper *nix syntax ( mysecureshell ).

2) OMG does the documentation & man pages SUCK!!!!! Except for the fact that the conf file is fairly straight forward - god help you if you want detailed information on any of the commands ;-)
(ie: what all their options are, what files they touch, etc) In fact, at least 1 of their management commands is bugged (create user) - but I won't use any of their tools anyway...

Honestly - I can't understand why I had to go to this package anyway... the umask thing is a CLEAR bug, that no one is apparently fixing; and the ability to do a "virtual chroot" seems absolutely common sense to me - this is what chroot should have provided from day 1.

Then, I wouldn't have spent an entire week trying to get sftp to do what it should have done FROM WITHIN THE OFFICIAL DIST.!
(I also dislike having to go "outside" the dist, but I guess I'll live with that :)

TX for the great info!!

---

### Post by hyper_ch on 2008-08-29
well, good it works ;)

---

