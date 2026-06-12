---
title: "a feature i would like to see added to ssh"
date: 2019-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-04-26
i'm unsure where to post my thoughts on "a feature i would like to see added to ssh" but here goes.  mods, please move this if there is a more appropriate place.

the feature i would like to see added to ssh is the ability to run a script that interacts with the remote session and, it it does end that session and instead just exits with a status of 0 (no error) ssh will keep this session connected and carry out normal interaction with the terminal that ssh was start with on stdin, stdout, and stderr.  the idea is to have to ability to start up things on the remote that can only be start with at least some of that process done interactively and/or timed and/or in response to output from the remote session.  of course this would be an option.  if the script exits with an error status or sends the escape character followed by a '.' then ssh will disconnect the session.  if the remote session drops the connect, then ssh will close the pipe with the script if it is still active and exit like it normally does.  the script may then do other stuff like recording logs, etc.  if the new option is not used, then ssh will behave like it usually does.

---

### Post by QIII on 2019-04-26
More appropriate here.  :)

---

### Post by DuckHook on 2019-04-26
I'm sure you've been around long enough to know that the devs don't visit here. As a discussion thread, it may be of interest to forum members, but as a request, you would do better with the openssh mailing list [here]("https://www.openssh.com/list.html").

---

### Post by Skaperen on 2019-04-27
yes,i know devs, in general, prefer to hang out with other devs, and that means they are not here, or other public forums.

i want to get feedback from potential users before i try to make the suggestion to devs.  maybe that feedback can justify the idea, or show it's not worth it.  maybe someone will want to hack the source and make the patch.  devs tend to like things that come with a source patch (that works the right way and follows their coding style).  i don't know if i could do that, myself.

---

