---
title: "How can I update my tomboy notes from local to webserver?"
date: 2010-05-01
forum: Ubuntu One (CLOSED)
---

### Post by kamui0523 on 2010-05-01
It's always update my local file from web server,which is not my want it.
I have beem overwrited by web server many times.It's made me so mad.
Is there any way to just only update webserver from local and keep my local files original?

---

### Post by joshuahoover on 2010-05-03
> **kamui0523 said:**
> It's always update my local file from web server,which is not my want it.
I have beem overwrited by web server many times.It's made me so mad.
Is there any way to just only update webserver from local and keep my local files original?

I'm not sure why the notes on the web are overwriting your local notes. This should not happen unless the notes on the web are newer than your local notes. Then it should prompt you which version you want to keep. If you want to try to force your local notes to overwrite the ones that are on the server right now, you can try the following:

[LIST=1]
[*]Quit Tomboy
[*]Backup your local Tomboy notes. Run the following command in a terminal session (Applications->Accessories->Terminal): cp -r ~/.local/share/tomboy ~/.local/share/tomboy_backup
[*]Go to the web UI and delete your notes there: [https://one.ubuntu.com/notes](https://one.ubuntu.com/notes)
[*]Open Tomboy and sync your notes
[*]If your notes are gone in Tomboy, quit Tomboy and run the following in a terminal session: 
rm -r ~/.local/share/tomboy
cp -r ~/.local/share/tomboy_back ~/.local/share/tomboy
[*]Open Tomboy and sync your notes
[/LIST]
If this problem persists, please file a bug by doing the following:

[LIST=1]
[*]Quit Tomboy 
[*]Applications->Accessories->Terminal, and run: 

[LIST]
[*]tomboy --debug > ~/tomboy_debug.log 
[/LIST]
[*]Try to  reproduce the bug
[*]File a bug at: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)
[*]Attach ~/tomboy_debug.log to the bug report
[/LIST]
Thank you,

Joshua

---

