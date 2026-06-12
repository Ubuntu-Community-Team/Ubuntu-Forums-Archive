---
title: "MIT License: sublicensing"
date: 2016-05-06
forum: Ubuntu, Linux and OS Chat
---

### Post by dvrein on 2016-05-06
Hi, if I got a repository copy from a dev under MIT License, and modified/contribute/change the codes/files, then can I add my own copyright notice in the same LICENSE/COPYING file, or should I put it into a separate file like ORIG License, MAINTAINER License?

* I'm thinking to modify the LICENSE file like this. (only add my copyright, without changing anything else)
* Is this possible or acceptable?

```
copyright (c) 2016 Mr Owner
copyright (c) 2016 My name
```

Thanks for all help.

* I don't know which section of forum should I post, I think this section is the most related.

---

### Post by bapoumba on 2016-05-07
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not being a lawyer, and not knowing how extensive your modifications are, one starting point could be to contact Mr. Owner and see how they want it to be. MIT license text should be included in the readme or license bit (link below), Mr. Owner will remain the copyright holder of their original work, you should license (under the MIT License if you wish) your own part, and that part only. If your code is bundled within Mr Owner code, it could be a good idea to describe that somewhere.

Others may have better input, I mainly use CC. MIT License is quite permissive as to how you use the original code, but please do understand you cannot take ownership of it, only the code you modified. At least, that is how I've always been doing, so if I'm doing it wrong, I'd like to know :)

[https://opensource.org/licenses/mit-license.html](https://opensource.org/licenses/mit-license.html)

---

### Post by dvrein on 2016-05-07
[QUOTE=bapoumba]If your code is bundled within Mr Owner code, it could be a good idea to describe that somewhere.[/QUOTE]

That enlightening it. So I basically, use Mr. Owner code, and also bundled it with my code. Then, I provide the Mr. Owner license, and mine for the modified code only.

Is that correct?

Thanks

---

### Post by bapoumba on 2016-05-07
This is the way I understand it, and this is the way I do it. As I previously stated, I'm not a lawyer and there may be subtleties, I am not providing a legal counseling.
My own interpretation is that you can license your code, with MIT License or another one as MIT License is permissive. Documenting the part you modified is important so that Mr. Owner gets the licensing for the work they did, keeping the original license they choose for the original work they produced.
You may want to look at recent questions such as [http://programmers.stackexchange.com/questions/287921/is-this-the-correct-way-to-include-this-mit-licensed-software-in-my-software](http://programmers.stackexchange.com/questions/287921/is-this-the-correct-way-to-include-this-mit-licensed-software-in-my-software)
You'll see there is no clear cut answer.

If you look here : [https://opensource.com/opensourcecom-team](https://opensource.com/opensourcecom-team), Jono Bacon shows being in the team. May be he'll know or he'll can refer you to someone who knows :)

---

### Post by dvrein on 2016-05-07
Thank you :)

---

