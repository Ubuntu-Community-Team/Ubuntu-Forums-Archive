---
title: "Batch Variables"
date: 2010-04-21
forum: The Cafe
---

### Post by takisan on 2010-04-21
Hello World!

This may sound a little bit weird because I'm an Ubuntu enthusiast currently using Windows XP, but I'm making a batch file that finds a drive, and then (this is where I'm stumped) in another batch file, I want to use that set variable.
My instincts are telling me just to use that same variable and try to not set it over in another file, but I think (like always) there's a chance that that's wrong.

Thanks for any assisstance.

---

### Post by Sporkman on 2010-04-21
The variable will carry over if you invoke the second script using "source", otherwise if you simply execute it it won't - you'd need to instead pass the variable value as an argument.

a.sh:

```
#!/bin/bash

myvar="blah blah"
source ./b.sh

```

b.sh:

```
#!/bin/bash

echo "myvar = $myvar"

```

(make both files executable)

Result:
> ./a.sh
myvar = blah blah


But when a.sh is:

```
#!/bin/bash

myvar="blah blah"
./b.sh

```

we get:

> ./a.sh
myvar =

---

### Post by RiceMonster on 2010-04-21
> **Sporkman said:**
> *snip*

Batch, not bash.

---

### Post by Sporkman on 2010-04-21
> **RiceMonster said:**
> Batch, not bash.

D'Oh!! :mad:

This gross misinterpretation on my part needs some Freudian analysis. Any interested parties, please proceed...

---

