---
title: "Text/Console-based dialog programming tools: anything more versatile than dialog?"
date: 2012-09-11
forum: Ubuntu Application Development
---

### Post by blavov on 2012-09-11
Hi everyone,
I'm looking for a tool to create text-mode (i.e. without X11 etc.), keyboard-driven dialog programs for specific configuration tasks. I already work with dialog, but it has limits when it comes to displaying more than one selection on the same page; plus, it cannot fill certain fields depending on input of other fields, check for syntax (i.e. whether input is a valid e-mail address, ip address, or domain name) and so on. I have looked at the ncurses and forms libraries, but you have to program almost everything yourself from scratch with those. 

Is there a program, library, or set of libraries with which I can, for example create a network configuration dialog where all I addresses are checked for validity on input and where I can, for example fill certain fields automatically depending on what the user types into "ip address", without having to program everything from scratch? I've seen many kits for this (like Qt, Gtk etc.), but I've found none which supports this on the text console. 

If you have any suggestions what to check out, please don't hesitate. 

Best regards, Pit.

---

### Post by SeijiSensei on 2012-09-11
I'd write a PHP application and access it from a browser.  Once the forms are complete, the application would generate the appropriate set of commands and use the exec() function to run them.

I believe most of the text-mode dialogs that less GUI-based Linux distros like RedHat employ are written in Python.

---

### Post by blavov on 2012-09-11
Thanks for the suggestion. I thought about PHP and HTML myself - but I know no non-awful text-mode browsers when it comes to handling forms, especially when the user in front of the screen is no computer wizard. Dialog menus, on the other hand are very clean and easy-to-use, but lack the complexity I need. 

I've never written a python program, but I'd consider changing that if I knew what interface they're using for creating dialogs/forms. Can you point me to any documentation on the matter? 

Cheers, Pit.

---

### Post by SeijiSensei on 2012-09-11
You could look at the code that RedHat uses for its "setup" command.  There's a multi-field dialog for network configuration that might prove helpful.  I'm pretty sure all that code is licensed under the GPL.

---

### Post by openfly on 2012-09-12
The python curses module is pretty decent.  But the learning curve can be steep.

---

