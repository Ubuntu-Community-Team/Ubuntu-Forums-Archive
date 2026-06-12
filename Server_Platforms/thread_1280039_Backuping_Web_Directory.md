---
title: "Backuping Web Directory"
date: 2009-10-01
forum: Server Platforms
---

### Post by TayfuN on 2009-10-01
Does anyone have good script for daily-weekly-monthly backuping of Web Directories ? I know I can just make backups with crontab in one command line, but I want a script that will make 7 backup file in daily dir, 4 in weekly and 12 in monthly. Maybe someone would share such script ? :popcorn:

---

### Post by undecim on 2009-10-01
Regular backups should be done with cron. I'm not sure I understand what you want with your directory setup though... You want a directory with daily, weekly, and monthly snapshots of the directory so that you can go back (for example) 3 weeks in the past and have a copy of each file that was there?

If so, I can modify my snapshot script which uses rsync to do that for you. It will also create hard links to files that haven't changed, so you won't need to use as much disk space.

---

### Post by TayfuN on 2009-10-02
Oh, that will be greate ! Thank you very much.

---

