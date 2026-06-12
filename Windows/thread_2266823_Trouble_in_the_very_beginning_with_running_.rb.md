---
title: "Trouble in the very beginning with running .rb"
date: 2015-02-25
forum: Windows
---

### Post by matthew75 on 2015-02-25
okay, so i used the railsinstaller to get ruby and i tried to make this simple file just "puts 2+3" and when i go to my irb i just drag and drop becuase doing cd never got it to work for me, but neither has this i just know its the right directory for the file. Anyways, when i drag it in there it puts the directory of the file then i hit enter and i believe its suppose to pop up and tell me 5. but when i hit enter this is what i get

"
irb(main):005:0> C:\Users\rando_000\Desktop\calc.rb
SyntaxError: (irb):5: syntax error, unexpected $undefined, expecting tSTRING_CON
TENT or tSTRING_DBEG or tSTRING_DVAR or tSTRING_END
C:\Users\rando_000\Desktop\calc.rb
   ^
        from F:/RailsInstaller/Ruby1.9.3/bin/irb:12:in `<main>'
irb(main):006:0>
"

---

### Post by TheFu on 2015-02-25
a) this isn't a Linux question - belongs in a different "Other OS" forum.
b) If you are going to be a Ruby programmer, you need to get used to working at a prompt and in a directory. Drop the GUI.  Ruby and Rails expect to have a project CWD - Current Working Directory - when running the programs.

I find people trying to learn Ruby on Windows fighting uphill. Best to just switch to Linux and learn it in the way it will be deployed. NOBODY - NOBODY - runs production ruby on Windows.

Sorry - I can't help with Windows problems.

---

### Post by oldos2er on 2015-02-25
Not an Ubuntu support question; moved to Other OS Support & Projects.

---

