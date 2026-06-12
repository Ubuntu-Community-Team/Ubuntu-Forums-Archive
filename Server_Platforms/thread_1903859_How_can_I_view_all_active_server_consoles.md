---
title: "How can I view all active server consoles"
date: 2012-01-03
forum: Server Platforms
---

### Post by sibleytr on 2012-01-03
I have a headless server (11.10) running backup jobs on different consoles (F1 through F6)

Is there a way to view all active consoles on the same monitor at the same time?


My goal is to have at least four different consoles running side by side (in a quad formation) by basically splitting the screen into four "windows" and being able to toggle through the consoles.

Any ideas?

---

### Post by Lars Noodén on 2012-01-03
You might be able to do something with panes in [tmux](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tmux.1.html) or [screen](http://manpages.ubuntu.com/manpages/oneiric/en/man1/screen.1.html).  You'd have to be logged into each console to do that, though.

---

### Post by sibleytr on 2012-01-04
tmux did the trick - thank you for your assistance.

---

