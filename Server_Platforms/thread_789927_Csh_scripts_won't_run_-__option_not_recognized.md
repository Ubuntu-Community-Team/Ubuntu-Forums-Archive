---
title: "Csh scripts won't run -  option not recognized"
date: 2008-05-11
forum: Server Platforms
---

### Post by newdejavu on 2008-05-11
I’m trying to run a a csh script.

I wrote a shell script and it worked fine yesterday.

The next time I log, I run the script “./rm_csh .” and get:

```
-'nknown option: `-

Usage: csh [ -bcdefilmnqstvVxX ] [ argument ... ].
```
 
When I run the script “csh –f rm_csh .”, I get:

foreach: Words not parenthesized.

I can’t figure out what’s going on.  The script works fine one day, the next day the line #!/bin/csh –f is not recognized.

This is the whole rm_csh script:

```

#!/bin/csh –      [COLOR="Red"]/*** fails on this line as ./rm_csh[/COLOR]
 
set todayDate=`date "+%m%d%Y"`

set thePath=${1}

foreach FILE (`ls ${thePath}/*_*.jpg`) 
    set fileDate = `echo ${FILE} | cut -f2 -d"_" | cut -f1 -d"."`

    if ("${fileDate}" != "${todayDate}") then

       rm -rf ${FILE}

    endif

end

```


Any ideas?  I’m thinking it’s the environment for some reason, but I don’t know how to fix it.

My server doesn’t recognize csh.

---

