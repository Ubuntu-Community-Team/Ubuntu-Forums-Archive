---
title: "Split Evolution into separate applications"
date: 2009-03-22
forum: Ubuntu Brainstorm
---

### Post by CarpKing on 2009-03-22
Evolution is a deeply integrated core component of the Gnome desktop, handling email as well as the user's address book, task list, and calender.  However, Evolution is also known for a clunky, complicated UI, and is mainly intended as a Outlook clone for the business world.  Such a program tries to do too much at once, and is not friendly to the home user.  Many users prefer instead to install programs like Thunderbird, but this also forces them to install more non-integrated apps for things like the calendar.  

The solution is to replace Evolution with a set of integrated applications covering different parts of its functionality and talking to its backend, EDS.  Applications that do this are already available, in the form of the Pimlico suite [*](http://www.pimlico-project.org/) and the newly released Anjal[*](http://blogs.gnome.org/sragavan/2009/03/18/announcing-anjal-the-new-mail-for-netbooks/).  

These programs follow the Unix philosophy of doing one thing and doing it well, and build on existing Gnome technologies to provide a well-integrated experience.  The will also help users who use alternate email clients continue to benefit from functions like the calendar that are not necessarily tied to email.

---

### Post by smartboyathome on 2009-03-22
This is something that you'd have to take to the Evolution developers, not Ubuntu's, since Ubuntu only packages Evolution.

---

### Post by CarpKing on 2009-03-22
Perhaps I should have come up with a better title.  It's not really a case of modifying the existing program so much as replacing it with other existing programs that use the same backend.  The only real modification I can think of is integrating Gnome calender so that clicking a date opens Dates instead of Evolution.

---

