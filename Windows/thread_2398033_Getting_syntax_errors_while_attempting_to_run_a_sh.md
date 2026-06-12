---
title: "Getting syntax errors while attempting to run a shell script"
date: 2018-08-06
forum: Windows
---

### Post by psychopath23 on 2018-08-06
Hi,

Unlike other instances I've searched for of syntax errors for a shell script (EOL not using unix format), I'm getting general syntax problems for code that has no syntax errors.

I downloaded win-bash from [http://win-bash.sourceforge.net/](http://win-bash.sourceforge.net/) to be able to run shell, which I can get into fine, I just can't execute the following code via a shell script:

#!/bin/bash

for ((i = 0; i <= 100; i++)); do
    echo "Number $i"
done

echo "Done"


I get the following errors
test.sh: syntax error near unexpected token '(('
test.sh: test.sh: line 3: 'for ((i = 0; i <= 100; i++)); do'

Any help would be appreciated, thanks.

---

### Post by spjackson on 2018-08-06
See FAQ [http://win-bash.sourceforge.net/](http://win-bash.sourceforge.net/)
"What differs win-bash from cygwin-bash?

First of all, you should keep in mind that win-bash is based on a old version of bash (1.14.2) while cygwin -bash is more or less up to date."

It's a fair bet that bash 1.14.2 didn't support this syntax.

For quite a few years now, for bash on Windows, I use git-bash (bash 4.3.42 in what I have installed).

---

### Post by psychopath23 on 2018-08-06
Thanks for the reply. I was initially going to install cygwin, but there's so much more content selection with its installer that I didn't want to bother with. I just want a fairly basic bash shell. I'll check out git-bash.

Thanks again.

---

