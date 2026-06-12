---
title: "Shared lib exists but not found by linker"
date: 2012-10-15
forum: Ubuntu Dev Link Forum
---

### Post by gerryg001 on 2012-10-15
A shared lib linking issue during c++ development. Laptop had Lucid-32 and was building apps with g++ and wxWidgets using eclipse. Upgraded to Ubuntu precise. Builds now will no longer link to wxWidgets shared libs, though fine with Boost and other libraries. Same "undefined reference" from linker when linking from command line.

Added verbose to g++ linking script and the log shows -L/usr/local/lib so it should be searched. Lib needed is shown there as -lwx_gtk2_core-2.8 which is the correct version.

Correct shared libs are installed, and can be found via "ldconfig -v". Using showelf and nm against the specific library and comparing to the error log, the references do exist in the library. All required soft links are present in /usr/local/lib, and "find -L -type l" sees no broken links. A link exists with a name of libwx_gtk2_core-2.8.so which should satisfy this with the proper naming.

Copied over a previously built executable under Lucid to this Precise system. It is able to find and use the same shared wxWidgets libs. Runs okay.

Removed all wxWidgets components, downloaded from their site and rebuilt/installed. No change in behavior.

This is not one app, but many with this problem. It still builds fine on a Lucid system.

No similar problem found on wxWidgets forums.

Any thoughts on where to look at this point?

---

### Post by spjackson on 2012-10-15
I suspect you need to change the order of the libraries in the link command. I think that the --as-needed flag for ld was off by default in Lucid but has been changed since to on. If you can't solve it, please post your link command.

---

### Post by gerryg001 on 2012-10-15
Oh groan! I must have looked at only the ordering in eclipse, and not the emitted build script... IDE's make one lazy, I guess, or I would have caught that early on.

Editing eclipse's emitted script and changing the lib ordering lets it link and run okay. I then confirmed the --as-needed flag change you mentioned as causing the issue.

Back in eclipse, you can add -Xlinker flags, but it puts them after the libs, so no joy there. In eclipse I had to change the command itself from "g++" to "g++ -Xlinker -no-as-needed" for the linker invocation. This should be okay in Lucid, so I only have one source without conditionals.

The reason only the wxWidgets libs were impacted is that they are declared under linker flags as:

[INDENT][/INDENT]`wx-config --unicode=no --debug=no --libs`

and that causes eclipse to run and emit that before the other libraries, and you can't change that ordering.

So, good catch, spjackson.
Thank you much.

---

