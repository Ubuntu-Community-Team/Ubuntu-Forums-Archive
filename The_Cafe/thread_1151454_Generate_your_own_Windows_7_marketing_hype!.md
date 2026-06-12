---
title: "Generate your own Windows 7 marketing hype!"
date: 2009-05-06
forum: The Cafe
---

### Post by monsterstack on 2009-05-06
Here you go, folks. DIY marketing.

```
[COLOR="DimGray"]#!/usr/bin/env python2.6[/COLOR]

[COLOR="Indigo"]from[/COLOR] [COLOR="Blue"]sys[/COLOR] [COLOR="Indigo"]import[/COLOR] [COLOR="Blue"]argv[/COLOR]

[COLOR="Indigo"]def[/COLOR] [COLOR="Olive"]marketing[/COLOR](current_version,new_version,competitor):
        text = """
$2 will be so much better than $1, for many reasons.
$2 will be faster, leaner, more secure, and will make you
more productive. We've improved on $1's excellent security
features to ensure that $2 will be the most secure edition yet.

$2 will have more themes, more features, and more usability options
than $1, which makes it the perfect reason to upgrade.

$2 will triumph over $3 on all these matters and much else besides!"""

        text = text.replace("$1",current_version)
        text = text.replace("$2",new_version)
        text = text.replace("$3",competitor)
        [COLOR="Indigo"]return[/COLOR] text

[COLOR="Indigo"]print[/COLOR] marketing(argv[1],argv[2],argv[3])
```

Now just go ahead and save that bit of text as marketing.py and run it as
```

python marketing.py "Windows Vista" "Windows 7" "Linux"
```

Then again, you might just as easily go back in time by running

```
python marketing.py "Windows XP" "Windows Vista" "Linux"
```

Or perhaps you might just want to turn the universe up-side down!

```
python marketing.py "OpenBSD 4.4" "Microsoft Bob" "zOS"
```

---

### Post by pwnst*r on 2009-05-06
i find it odd that there are only four pieces left.  i wonder what it's like on Monday?

---

