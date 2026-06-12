---
title: "Cant' start MySQL on Dell Mini 10v (Ubuntu 8.04)"
date: 2009-07-08
forum: Server Platforms
---

### Post by hgeis on 2009-07-08
Hi,

When trying to start Mysql on my new Dell Mini 10v under Ubuntu 8.04 I get the following error message:

[B]sudo /etc/init.d/mysql start
[/B]
[B]/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
[/B]
That's the code of the script at line 84

if [ "$INITOUTPUT" = "yes" ]; then
        if log_use_fancy_output && $TPUT xenl >/dev/null 2>&1; then
            COLS=`$TPUT cols`
            if [ "$COLS" ] && [ "$COLS" -gt 6 ]; then
                COL=`$EXPR $COLS - 7`
            else
                COLS=80
                COL=73

I have seen quite a number of postings on this problem on various Ubuntu forums, but no solution so far.

Any idea?

Thanks in advance and regards.

H.

---

### Post by slugmax on 2009-07-08
Try getting rid of the 'set -u' line in the /etc/init.d/mysql script. From the Bash manpage:

"-u      Treat unset variables as an error when performing parameter expansion.  If expansion is attempted on an unset variable, the shell prints an error message, and, if not interactive, exits with a non-zero status."

Here is an experiment:

```

dmaxwell@kaylee:~$ echo $FOO

dmaxwell@kaylee:~$ set -u
dmaxwell@kaylee:~$ echo $FOO
bash: FOO: unbound variable

```

---

### Post by hgeis on 2009-07-09
Hi,

it did work. **Thank you.**

H.

---

