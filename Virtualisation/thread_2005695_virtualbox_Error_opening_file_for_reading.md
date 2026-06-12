---
title: "virtualbox: Error opening file for reading"
date: 2012-06-18
forum: Virtualisation
---

### Post by ThePythonicCow on 2012-06-18
I have just upgraded my Kubuntu system from 11.10 to 12.04, and then installed virtualbox.   I have gotten far enough to install Oracle_VM_VirtualBox_Extension_Pack, so that I can use USB 2.0, and to add myself to the vboxusers group.  I have not yet started installing Windows XP inside my new virtualbox.

Everytime I start up virtualbox, I get the error:
```
Error opening file for reading: Permission denied
```Running strace on this process (well, seems I have to run it on the shell within which I start virtualbox) I can see the following:

```
15128 open("/proc/self/auxv", O_RDONLY) = -1 EACCES (Permission denied)
15128 dup(2)                            = 19
15128 fcntl(19, F_GETFL)                = 0x8002 (flags O_RDWR|O_LARGEFILE)
15128 fstat(19, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 0), ...}) = 0
15128 mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fe3d6b13000
15128 lseek(19, 0, SEEK_CUR)            = -1 ESPIPE (Illegal seek)
15128 write(19, "Error opening file for reading: "..., 50) = 50
15128 close(19)                         = 0
```This error does not seem to cause a problem, and the virtualbox session proceeds without further problems.

Looking about the web, I see that virtualbox is apparently trying to open /proc/self/auxv in order to determine some system capabilities, and that it is realized that this is not a reliable method -- auxv may or may not be readable.

In my situation, auxv is reliably NOT readable :).

The following shell command reliably shows the contents of what is, I suspect, the desired auxv information:
```
LD_SHOW_AUXV=1 /bin/true
```For example on my Kubuntu 12.04 amd64 system, it shows:
```
AT_SYSINFO_EHDR: 0x7fffcd7c4000
AT_HWCAP:        bfebfbff
AT_PAGESZ:       4096
AT_CLKTCK:       100
AT_PHDR:         0x400040
AT_PHENT:        56
AT_PHNUM:        9
AT_BASE:         0x7ffc2640c000
AT_FLAGS:        0x0
AT_ENTRY:        0x401134
AT_UID:          1000
AT_EUID:         1000
AT_GID:          1000
AT_EGID:         1000
AT_SECURE:       0
AT_RANDOM:       0x7fffcd772489
AT_EXECFN:       /bin/true
AT_PLATFORM:     x86_64
```The following code might provide a useful and reliable means of parsing
this auxv information:
```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

/*
 * The following flgets() and examine_auxv() routines are Copyright
 * 2006 and 2012 respectively by Paul Jackson <pj@usa.net>.
 *
 * These routines are free software; you can redistribute them and/or
 * modify them under the terms of the GNU Lesser General Public
 * License as published by the Free Software Foundation; either
 * version 2 of the License, or (at your option) any later version.
 *
 * This library is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 * Lesser General Public License for more details.
 *
 * You may obtain a copy of this license from: <http://www.gnu.org/licenses/>.
 */

/*
 * char *flgets(char *buf, int buflen, FILE *fp)
 *
 * Obtain one line from input file fp.  Copy up to first
 * buflen-1 chars of line into buffer buf, discarding rest
 * of line.  Stop reading at newline, discarding newline.
 * Nul terminate result and return pointer to buffer buf
 * on success, or NULL if nothing more to read or failure.
 *
 * Paul Jackson
 * pj@usa.net
 * 20 Feb 2006
 */

static char *flgets(char *buf, int buflen, FILE * fp)
{
    int c = -1;
    char *bp;

    bp = buf;
    while ((--buflen > 0) && ((c = getc(fp)) >= 0)) {
        if (c == '\n')
            goto newline;
        *bp++ = c;
    }
    if ((c < 0) && (bp == buf))
        return NULL;

    if (c > 0) {
        while ((c = getc(fp)) >= 0) {
            if (c == '\n')
                break;
        }
    }

newline:
    *bp++ = '\0';
    return buf;
}

/*
 * int examine_auxv(const char *pattern, char *buf, int buflen)
 *
 * Examine /proc/self/auxv, as formatted in the manner
 * seen by running the command:
 *    LD_SHOW_AUXV=1 /bin/true
 * Return the first line that has some substring matching
 * the input "pattern".  Return up to the first (buflen-1)
 * characters of that line, nul-terminated, in the provided
 * buffer "buf".
 *
 * Only the first buflen-1 characters of each line are examined
 * for the input pattern.  If that pattern is not entirely
 * contained within those buflen-1 characters, it will not
 * found on that line.
 *
 * Return zero if a match is found and placed in buf, else
 * return -1 and (in most cases - see popen(3) man page)
 * set errno appropriately.  If no match is found, the
 * buffer buf is overwritten with the last line of input
 * from the above command.
 *
 * Paul Jackson
 * pj@usa.net
 * 17 June 2012
 */

int examine_auxv(const char *pattern, char *buf, int buflen)
{
    char *bp;
    FILE *fp;

    fp = popen("LD_SHOW_AUXV=1 /bin/true", "r");
    while ((bp = flgets(buf, buflen, fp)) != NULL) {
        if (strstr(bp, pattern) != NULL) {
            pclose(fp);
            return 0;
        }
    }
    pclose(fp);
    return -1;
}

/*
 * Test case for above:
 */

#define BUFLEN 256
char buf[BUFLEN];

int main(int argc, char *argv[])
{
    int i;

    for (i = 1; i < argc; i++) {
        if (examine_auxv(argv[i], buf, BUFLEN) == 0)
            printf ("%s ==> %s\n", argv[i], buf);
    }
    exit(0);
}
```

Bug report link:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1014487](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1014487)

---

### Post by CharlesA on 2012-06-26
I was able to reproduce this on my vbox machine. It seems to only occur if you try to access the VBox GUI itself, whether it is to access the vbox manager or start a VM from the command line.

Tested on VBox 4.1.18 with extension pack installed on 12.04 server x64.

---

