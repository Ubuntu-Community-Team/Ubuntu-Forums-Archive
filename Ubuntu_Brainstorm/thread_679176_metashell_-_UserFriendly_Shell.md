---
title: "metashell - UserFriendly Shell"
date: 2008-01-26
forum: Ubuntu Brainstorm
---

### Post by Pysco on 2008-01-26
Hello Fellow Ubuntu Users:

     I hope this is the right section to post this?  It was between this, the Programming forum, or the Cafe?  Anyway, if this is not the right choice, please move or direct me to the correct area, thanks.  The important part, after the jump.

     I found this project, "metashell" on Freshmeat/Source Forge.  I wanted to share it with the Ubuntu community.

Directly from the [metashell]("http://www.themetashell.com") website:

[INDENT][I]metashell is a lightweight, heavy punch, interactive, intelligent command-line shell. The amazing difference with metashell lies in its ability to determine a file's datatype, and automatically run your desired applications.

metashell uses file datatypes (mime types) to determine a files type, and then using user defined applications automatically opens the files. Making the user experience in a shell easier and more user-friendly, while adding robust power to the CLI gurus of yesterday, today, and tomorrow.

STATUS: Beta (Beta has been released)  [/I][/INDENT]

     As you can see the project is still only is Beta, but development seems to be active (at least since the initial beta release).  I've also been using the shell for the past few days, and am currently using the latest version (0.03b).  Minus a minor installation bug, and a dependency not included in the Ubuntu repository, everything seems to work great.  And it does seem like it could be (albeit with a bit of work) a replacement as mine (and hopefully) your shell.

     The shell is honestly extremely user-friendly, but still contains the normal *nix power.  It just makes execution and file management a breeze.  You can still pipe commands, redirect output, background and union commands, etc.  The ground-breaking feature is really the way you work with files.

     You simply type in a filename, and based on its mimetype (and your configuration) the file is automatically open/executed through the default application (based on your ~/.msh_apps setting).  No more do you have to cat a file, or look through its contents.  The shell makes this an easy and seamless process.  It even will change directory, without you typing 'cd' (although you can still use 'cd' if desired).

     All of your normal commands/applications will function, (ls, cd, nano, cat, rm, mv, ln, cp, etc).  But you can now move around, and manage files a bit easier.

     I feel this will make the shell a far less "scary" place for new Linux users.  (I'll refrain from using the term noob, as I too am new to Linux).  It will allow them to use it to open and edit files, without learning an absurd amount of information before hand.  Allowing them to get the task done, and learn at a later time.  And although I feel learning is important, and they will eventually need to know the "hard way" this should be a good start.

     This seems to also be the direction Ubuntu is traveling, thus the reason I am posting this here.  Ubuntu is "Linux for human beings" and metashell seems to be "The Linux Shell for human beings".  Things "Just Work (tm?)".  Just like double-clicking, you enter a filename and things happen, no questions asked.

     The other cool part, is the default settings shipped, are for Ubuntu (Gnome), therefore Gnome GUI applications are opened for each filetype.  I really think Ubuntu users will benefit from this project.

     All that being said, beyond just telling you about the project, I have a question.  What are the chances of something like this shell or another user-friend shell making it into the Ubuntu distribution?  Even if not as a default?

     Please take a look, and give your feedback.  The Project Owner, is rather responsive, via email.  Plus let me know what you think, and the possibility of inclusion into Ubuntu.

Information:
Website:  [http://www.themetashell.com](http://www.themetashell.com)
Source Forge:  [http://metashell.sf.net](http://metashell.sf.net)

Thanks,
Pysco

---

### Post by 23meg on 2008-01-26
> **Pysco]I feel this will make the shell a far less "scary" place for new Linux users. (I'll refrain from using the term noob, as I too am new to Linux). It will allow them to use it to open and edit files, without learning an absurd amount of information before hand. Allowing them to get the task done, and learn at a later time. [/QUOTE]

Opening files from the terminal with the associated application is pretty simple (just prepend "xdg-open" to the file name) said:**
> and they will eventually need to know the "hard way" 

Will they? 

[QUOTE=Pysco]This seems to also be the direction Ubuntu is traveling, thus the reason I am posting this here. Ubuntu is "Linux for human beings" and metashell seems to be "The Linux Shell for human beings". Things "Just Work (tm?)". Just like double-clicking, you enter a filename and things happen, no questions asked.[/QUOTE]

Sure, it's convenient, but the added convenience is a corner case. The direction Ubuntu is going is rather removing the need to use the CLI for common tasks altogether. While a more friendly CLI can help, I don't think changing the default shell (which has only recently been done, with plenty of migration headaches) is warranted for this little added convenience.

[QUOTE=Pysco]All that being said, beyond just telling you about the project, I have a question. What are the chances of something like this shell or another user-friend shell making it into the Ubuntu distribution? Even if not as a default?[/QUOTE]

As the default shell, little chance. But inclusion in Universe would just take someone to package it.

---

