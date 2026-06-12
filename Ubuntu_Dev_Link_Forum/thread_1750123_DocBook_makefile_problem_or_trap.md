---
title: "DocBook makefile problem or trap?"
date: 2011-05-05
forum: Ubuntu Dev Link Forum
---

### Post by dudy on 2011-05-05
Running Makefile from linux-2.6.37.y/Documentation/DocBook deleted my /media folder, where also my external HDD was mounted and I lost all data!!! :mad: What did I wrong?

I run following:
declare -x srctree=../..
make htmldocs

Mentioned Makefile contains '@rm -rf $@ $(patsubst %.html,%,$@)' which generates 'rm -rf /media.html /media'.

When I invoke for example 'make -n htmldocs', I can see more 'rm -rf /_name.html /_name' commands, where _name is a common word like 'networking' etc.

What's wrong? Was it my fault or /media folder is a potential victim for such operations?

Thanks in advance!

---

