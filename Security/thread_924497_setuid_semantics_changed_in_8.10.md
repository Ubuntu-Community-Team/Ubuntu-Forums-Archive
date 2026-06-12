---
title: "setuid semantics changed in 8.10?"
date: 2008-09-19
forum: Security
---

### Post by LarryHastings on 2008-09-19
I've been using Ubuntu as my daily OS since 7.04.  I have to use the Juniper VPN software for work, which includes "ncsvc", a setuid program to drive the tun virtual network device.  This worked fine until I got to 8.10.

I eventually figured out the first piece of the puzzle: the semantics of setuid seem to have changed for 8.10.  It seems that 8.10 requires setuid programs to be readable as well as executable.  I changed ncsvc from 711 to 755 and it got past that problem.  (It still doesn't work, sigh, but that's a question for another day.)

Here's a test case.  I compiled the following program, uid.c:```
#include <stdio.h>
#include <string.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
  FILE *f;
  char buffer[256];
  sprintf(buffer, "Hello there, I'm uid %d, euid %d.\n", getuid(), geteuid());
  puts(buffer);
  f = fopen("foo", "wt");
  fwrite(buffer, 1, strlen(buffer), f);
  fclose(f);
  return 0;
}
```I then "sudo bash" and run```
# chown root ./uid
# chgrp root ./uid
# chmod 711 ./uid
# chmod u+s ./uid
# chmod g+s ./uid
# ls -l ./uid
-rws--s--x 1 root root 9346 2008-09-19 12:34 ./uid

```
I then exit from the su'd bash shell and run "% ./uid".

If I'm on 8.04, it prints out "Hello there, I'm uid 1000, euid 0.".  If I'm on 8.10, I get an error message: "zsh: permission denied: ./uid".

If I su again and make it 755:```
# chmod 755 ./uid
# chmod u+s ./uid
# chmod g+s ./uid
# ls -l ./uid
-rwsr-sr-x 1 root root 9346 2008-09-19 12:34 ./uid

```then I can run it as myself and it works.

I'm a bit surprised by this.  I figured the semantics of setuid were pretty well set in stone by now.  Why did this change?

---

### Post by cariboo on 2008-09-19
You would be better off asking your question here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

I see developers answering questions in this forum, where you virtually never see them answering questions anywhere else.

Jim

---

