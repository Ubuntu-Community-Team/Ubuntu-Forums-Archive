---
title: "GNU GPL for Open Source"
date: 2010-09-23
forum: Ubuntu Dev Link Forum
---

### Post by Feareilo on 2010-09-23
I wrote a little program that I'd like to publish as open source. However, I don't know how to do that. Is a simple copyleft notice enough?

---

### Post by Chronon on 2010-09-23
[http://www.gnu.org/licenses/gpl-howto.html](http://www.gnu.org/licenses/gpl-howto.html)
[http://www.opensource.org/licenses/bsd-license.php](http://www.opensource.org/licenses/bsd-license.php)

Creative Commons also has various licenses that you might consider.

---

### Post by Feareilo on 2010-09-23
> **Chronon said:**
> [http://www.gnu.org/licenses/gpl-howto.html](http://www.gnu.org/licenses/gpl-howto.html)
[http://www.opensource.org/licenses/bsd-license.php](http://www.opensource.org/licenses/bsd-license.php)

Creative Commons also has various licenses that you might consider.

Thank you. I had already read that link but I did not express my question in the right way. Is it really that easy? Does that cover me worldwide or only my country of origin (Mexico)?

By the way, where should I include the GNU GPL? In the source code? That seems odd because the license must be even longer than my software's code. Should I bundle both the source code and the license on a zip/rar file?

---

### Post by dv3500ea on 2010-09-24
> **Feareilo said:**
> Thank you. I had already read that link but I did not express my question in the right way. Is it really that easy? Does that cover me worldwide or only my country of origin (Mexico)?

By the way, where should I include the GNU GPL? In the source code? That seems odd because the license must be even longer than my software's code. Should I bundle both the source code and the license on a zip/rar file?

The GPL covers you worldwide.

You can add a shortened version of the GPL to your source files like so:
```

#       Copyright 2010 NAME <EMAIL>
#       
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 3 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, see <http://www.gnu.org/licenses> or write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.
#       On some systems, a copy of the GPL may already exist in /usr/share/common-licenses

```

You do not need to bundle the full licence with the program if you are distributing for Debian/Ubuntu because a copy of the GPL already exists in /usr/share/common-licenses. If you aren't sure about whether you need to include the full licence, bundle a plain text version of the licence with the program in a source code archive.

Do NOT use a .rar file because it is a proprietary format. .tar.gz is the norm for source code archives.

If the source code is shorter than this shortened version of the licence, you should consider releasing the code to the public domain.

---

### Post by Feareilo on 2010-09-25
Thank you for the very helpful reply.

Actually, it's a blackberry app. It's a J2ME jar. I guess I'll have to use the short version on the source code and bundle it with the large verison on a .tar.gz

Again, thank you.

---

