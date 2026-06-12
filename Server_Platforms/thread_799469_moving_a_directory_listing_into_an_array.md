---
title: "moving a directory listing into an array"
date: 2008-05-19
forum: Server Platforms
---

### Post by Yulquen on 2008-05-19
hi,

do anyone of you know of a smarter way to do this?

this works:
ls -l -R -a | grep './' | tr -d ':' >~/bin/buffer

num=$(cat ~/bin/buffer|wc -l)

until [ $num = 0 ];     do
        array[$num]=$(sed -n -e "$num"p ~/bin/buffer)
        num=$(expr $num - 1)
done

but the loop is very slow.
the ls pipe completes in a second, but the loop uses about 35 seconds to complete when buffer is 3200 lines.

is it possible to to it faster? I need this to speed up a 
larger script.

thanks in advance for any answers.

---

### Post by jklm988 on 2008-05-19
You write very well, support you![premature ejaculation](http://www.penisworld.net) [penis enlargement](http://www.penisworld.net)[guild wars gold](http://www.gamezmoney.com)

---

