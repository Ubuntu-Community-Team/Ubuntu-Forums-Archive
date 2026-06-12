---
title: "Libnewt usage"
date: 2011-10-11
forum: Ubuntu Dev Link Forum
---

### Post by Constantine85 on 2011-10-11
Hi everyone, I'm having Ubuntu-specific bug when using libnewt: the scrollbar doesn't show. Code works OK in Fedora, I simply can't figure out what's wrong with it.
I've isolated the problem to following code example:

#include <newt.h>
#include <stdio.h>
 int main(void) {
 newtComponent form, text, button;
 newtInit();
 newtCls();
 text = newtTextbox(0, 0, 30, 5, NEWT_FLAG_SCROLL | NEWT_FLAG_WRAP);
 newtTextboxSetText(text,"Some really long text there that  should fit multiple lines in order for scroll to have purpose, it's not  shown there but it works, so you can scroll text without seeing actual  scrollbar");
 button = newtButton(20, 5 + 2, "Ok");
  newtOpenWindow(5, 5, 34,
   12, "Test Texbox");
  form = newtForm(NULL, NULL, 0);
 newtFormAddComponents(form, text, button, NULL);
  newtRunForm(form);
 newtFormDestroy(form);
 newtFinished();
 return 0;
}


Maybe it's a bug which needs fixing?

---

