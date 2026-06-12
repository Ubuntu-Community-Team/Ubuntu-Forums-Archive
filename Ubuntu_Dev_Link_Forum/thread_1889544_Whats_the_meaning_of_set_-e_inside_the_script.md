---
title: "Whats the meaning of set -e inside the script"
date: 2011-12-01
forum: Ubuntu Dev Link Forum
---

### Post by jao_madn on 2011-12-01
Hi,

I would like to ask about the meaning or purpose of set -e in the script bash, Does it mean if a wrong command in the script it will close or exit the script without continuation thats what happen if i set it in the terminal.

---

### Post by Lars Noodén on 2011-12-01
It is hard to find, but it's in the manual page for [bash](http://manpages.ubuntu.com/manpages/precise/en/man1/bash.1.html):

[indent][i]
"-e      Exit  immediately  if a pipeline (which may consist of a
                      single simple command),  a subshell command enclosed  in
                      parentheses,  or one of the commands executed as part of
                      a command list enclosed by  braces  (see  SHELL  GRAMMAR
                      above) exits with a non-zero status.  The shell does not
                      exit if the command that fails is part  of  the  command
                      list  immediately  following  a  while or until keyword,
                      part of the test  following  the  if  or  elif  reserved
                      words,  part  of any command executed in a && or || list
                      except the command following the final  &&  or  ||,  any
                      command  in a pipeline but the last, or if the command's
                      return value is being inverted with !.  A trap  on  ERR,
                      if set, is executed before the shell exits.  This option
                      applies to  the  shell  environment  and  each  subshell
                      environment    separately    (see    COMMAND   EXECUTION
                      ENVIRONMENT above), and  may  cause  subshells  to  exit
                      before executing all the commands in the subshell."[/i]
[/indent]

---

