---
title: "Backup Solution suggestion"
date: 2009-01-28
forum: Ubuntu Brainstorm
---

### Post by goblinlord on 2009-01-28
I was reading over:
[https://wiki.ubuntu.com/FoundationsTeam/Specs/Backup](https://wiki.ubuntu.com/FoundationsTeam/Specs/Backup)

I believe I have a suggestion for backups.  What recording installed package information.  On a restore being able to completely recover without needing to actually backup the installed packages (seeing as they are already stored via repositories).

  This could be a viable option that would be nice for reducing the size of backups and could be a feature that could be enabled and disabled.

  Installed package information could be collected and then any packages not found in the repositories could be optionally stored.  If non-rep packages the user could be warned and prompted to store or not as well as a list of them printed out.  Also, any configuration files that are setup during install.  This would make reinstallation much smoother as after a fresh install all packages previously installed could be easily restored.  Also, any configuration files that are setup during install.

  At this point, the users Home folder could be saved with all multimedia files or large files being optionally backed up.  This can be dealt with by a simple prompt for the user once and then store in a configuration for optionally changing later.  This would then need to have a list of extensions that you want excluded and a size limit for files.  Lastly, you can have a complete backup for a specified folder optionally (this looks as it is already being looked at).

  These things would take care of fresh installation all they way to bringing you back with your previous configuration as well as have the option of restoring multimedia.

  These backups could be divided into 4 types.

      Core System (installed packages & system config)
      User Profile and Documents (excludes certain files)
      User Multimedia
      Specified Folder (Complete backup)

  Each of which could be stored seperately.  This being in just different files in a single folder or on seperate medium all together (differant HDDs or even burned seperately or together on a CD/DVD).

  Some of this has already been suggested and I appologize if any of it is repeat suggestions.  I would not mind assisting in development though my programming skills are rather limited and I have only been self-taught.  I do have decent shell scripting experience but still probably not up to par with many programers actually working on any projects.

  I am most interested in this as I have not really had problems myself before but didn't feel a restore was ever as "streamlined" as it could be.  Also, though I never had issues friends have had issues because they didn't understand a lot of the inner workings.


I would also like to reference my suggestion on brainstorm.ubuntu.com:

[http://brainstorm.ubuntu.com/idea/17488](http://brainstorm.ubuntu.com/idea/17488)
solution #3

---

