---
title: "Starting an open source php framework"
date: 2007-11-08
forum: The Cafe
---

### Post by samb0057 on 2007-11-08
I know there's cakephp, symfony, etc but i am looking for something more advanced and scalable

1: The ability to divide a site into sections (admin,public,advertisers,etc). Each section will have the capability to have its own configuration, initialization procedures, stylesheets, etc. Sections will also be in heirarchy (configuration from a parent section will be inherited or overwritten by a child section).

2: Automatic building of the database
Using 2 objects - models, and fields. Models have child fields. 
For example:
Model user
   field username
   field password

This will simplify many things, automatic building of the database can specify mysql maxlengths based on the fields. Validation is then easy because the validation properties are already set in the field object. Data is automatically validated when trying to use the model -> save() function. You only have to specify fields in one place, and from that your entire application (as well as the database) uses that specification

3: Maximum security and strictness. From what i've seen, the other frameworks don't really do this. As i have it now, all variables except _SERVER, _POST, etc. are automatically destroyed when the script is run. two globals exist, $mod and $cfg (mod for module cfg, cfg for application cfg). Any and all input is validated 100% (a malformed query string or attempted posting of a non-existent field throws an error). Error reporting is strict, allowing for no security slip-ups. The one thing about php that annoys me is that it is very easy to make an incredibly insecure application (register globals? come on).


I have been working on this for a couple of months now, and last time i checked i had over 9000 lines of code. if anyone else is interested in helping out, let me know. everything will be free and open source (i'm thinking gpl).

---

