---
title: "BASH &quot;history list&quot; never clears??"
date: 2011-08-07
forum: Security
---

### Post by kevcoder on 2011-08-07
...using ubuntu 10.04 and still learning

last night I used the shell to shutdown my pc ```
sudo shutdown -h 0
```and this morning, after physically turning the machine on, I go to the CLI and hit the up arrow key by mistake and viola!! there are all of the commands I issued yesterday.


[LIST=1]
[*]What's the point of that?
[*]If every keystroke is being cached, what about the password I typed for the sudo command?
[*]Can this "history" be cleared?
[*]this is only my home pc, but could another user, besides obviously root, see the commands of any other use and what group membership is that?
[/LIST]

---

### Post by SoFl W on 2011-08-07
I use command history often.
Your password is not logged.
No one can see your history but the user and of course root.
To delete it, [see this]("http://www.foogazi.com/2008/06/25/how-to-delete-bash-history/").

You can limit the history size by editing HISTSIZE in the .bashrc file

---

### Post by haqking on 2011-08-07
> **kevcoder said:**
> ...using ubuntu 10.04 and still learning

last night I used the shell to shutdown my pc ```
sudo shutdown -h 0
```and this morning, after physically turning the machine on, I go to the CLI and hit the up arrow key by mistake and viola!! there are all of the commands I issued yesterday.


[LIST=1]
[*]What's the point of that?
[*]If every keystroke is being cached, what about the password I typed for the sudo command?
[*]Can this "history" be cleared?
[*]this is only my home pc, but could another user, besides obviously root, see the commands of any other use and what group membership is that?
[/LIST]


1. the point is so you dont have to retype long or used often commands.
2. not all keystrokes are stored, you can not cycle through to obtain your password
3. yes it can be cleared with history -c from terminal
4. the bash history for your bash is stored in a file under your profile

---

### Post by Thewhistlingwind on 2011-08-08
> **haqking said:**
> 1. the point is so you dont have to retype long or used often commands.
2. not all keystrokes are stored, you can not cycle through to obtain your password
3. yes it can be cleared with history -c from terminal
4. the bash history for your bash is stored in a file under your profile

On 4. I remember being able to view other users home directories by default in Ubuntu. Might I suggest changing your home directories access rights so other users can't snoop?

---

### Post by haqking on 2011-08-08
> **Thewhistlingwind said:**
> On 4. I remember being able to view other users home directories by default in Ubuntu. Might I suggest changing your home directories access rights so other users can't snoop?

yes well a user can view the contents of the home folder though you could encrypt it yes.

But by default yes you can view the home folder, but you cant view the contents of the bash_history file of that user if you only a user.

---

### Post by AlphaLexman on 2011-08-08
> **haqking said:**
> yes well a user can view the contents of the home folder though you could encrypt it yes.

But by default yes you can view the home folder, but you cant view the contents of the bash_history file of that user if you only a user.
haqking is 100% correct, the permissions of '~/.bash_history' are by default '**-rw-------**' which means that ONLY the root user or the owner can read or write the file at all. Absolutely no other user can read your history, nor can you read any other user's history (without manual changes that would allow such access).

Your ~/.bash_history file is secure.

---

