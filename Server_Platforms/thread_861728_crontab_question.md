---
title: "crontab question"
date: 2008-07-16
forum: Server Platforms
---

### Post by johnelle on 2008-07-16
Still getting used to Ubuntu after years of Fedora.  I was trying to set-up the Drupal cron job and even though the entry shows up when I do a sudo crontab -l and the command is valid it never seems to execute. Never had this happen before so I'm not sure how to debug this.

One other annoyance is that I can't seem to get -e to use a reasonable editor by setting the VISUAL and/or EDITOR.

Suggestions welcome.

---

### Post by pauper on 2008-07-18
1) Post the command you trying to execute as cron job.

2) This command lets you choose a default editor:

```
sudo update-alternatives --config editor

```

The current choice is marked with a (*) and the choice with the highest
priority with a (+).

OR

If you find nano, vim, emacs too tough to use you may opt for gedit, for 
example, instead. This will add "export EDITOR=gedit" variable and a new line
before it--just to keep things neat.

```
echo -e "\nexport EDITOR=gedit" >> ~/.bashrc
```

The latter command will overrule the former one.

Run this command afterwards to make bash reread configs.

```
bash
```

If you stick with any GUI editor use the following command from now on:

```
gksudo "crontab -e"
```

---

### Post by johnelle on 2008-07-19
Thanks for the editor command...switched to vi.

Having not looked at it for a few days I reviewed the command the URL wasn't quite right.  So I will retry with the valid command.

---

### Post by hyper_ch on 2008-07-19
I normally create a cron.txt into which I add the cron commands and then add it to the according user:

```

crontab cron.txt

```
for the current user or

```

sudo crontab -u USER cron.txt

```

---

