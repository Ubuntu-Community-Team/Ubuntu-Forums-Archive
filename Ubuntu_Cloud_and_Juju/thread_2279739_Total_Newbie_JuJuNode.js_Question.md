---
title: "Total Newbie JuJu/Node.js Question"
date: 2015-05-25
forum: Ubuntu Cloud and Juju
---

### Post by Jamie_Poitra on 2015-05-25
I'm trying to follow the docs here:

[https://jujucharms.com/docs/devel/howto-node](https://jujucharms.com/docs/devel/howto-node)

And am running into an issue with this line:

```
juju deploy --config myapp.yaml node-app myapp
```

I've created a myapp.yaml file and added a github URL to a sample Node.js app but when I try to run the command I get this:

```
Added charm "cs:precise/node-app-10" to the environment.
ERROR no settings found for "myapp"
```

Theres no mention of this possibility in the docs and I'm unable to find anyone mentioning something similar.

I've been able to run other JuJu charms successfully.  For instance I've followed the Getting Started docs found here:

[https://jujucharms.com/docs/stable/getting-started](https://jujucharms.com/docs/stable/getting-started)

And everything worked perfectly.  

Thanks a ton to anyone who might be able to help.

---

### Post by blakehenderson on 2016-05-02
Check your .yaml file - make sure you did not use tabs when editing.
yaml does not accept tabs  - use spaces.
I was getting the same error and found that to be the solution.
A year late on this one but it might help someone else.

---

