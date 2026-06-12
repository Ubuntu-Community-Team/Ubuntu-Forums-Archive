---
title: "Thunar wish"
date: 2023-10-07
forum: Ubuntu, Linux and OS Chat
---

### Post by djhbrown2 on 2023-10-07
my wish isn't just for Thunar, it's for any file manager, and platform independent:
it's a human-use wish, which i may have to motivate because it may not be obvious why it's a good idea, so i will try:

we have files and folders, and paths - all very natural, even if paths can be a pain in the butt to manage when locations change.

to me, a file is a thing; it has a name, and an identity, and a location

now, when i move a thing from here to there because i am tidying up my room, the name of the thing doesn't change, not does its identity, but its location does.

but Thunar and Ubuntu don't know that - they are like small children that think a thing has ceased to exist once they can't see it any more where it used to be, and give me an error message "file not found".

so here's the solution (and this is my wish):

when a file is created, Ubuntu assigns it a unique id, a reference it keeps to itself, because i as a user don't need to know what that is, all i need to know is the file's name and location (and it's up to me and my program to remember what those are).

but when i talk to Ubuntu about a file's path/name, i don't mean it literally; i want Ubuntu to instead identify the file by its own (internal) unique id (and itself remember where it physically is), so if i later move that file from one conceptual place to another, Ubuntu will still be able to keep track of where it is and find it again when it's referenced by somewhere else before i moved it, without having to tell that somewhere else to update its link, because the internal link is to the file's unique id, NOT to a path/filename, which is only a conceptual (user interface) location, not necessarily a physical one

do you see what i mean, Thunar programmers?

can you fix it for me?  i know you can; it's a simple address translation database - but will you????

---

### Post by jeremy31 on 2023-10-07
Thread closed, duplicate of [https://ubuntuforums.org/showthread.php?t=2491413](https://ubuntuforums.org/showthread.php?t=2491413)

---

