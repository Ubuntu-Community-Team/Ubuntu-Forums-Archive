---
title: "Munin failed after upgrade from 16.04 LTS to 18.04.1 LTS"
date: 2018-09-21
forum: Server Platforms
---

### Post by hellspawn754 on 2018-09-21
Hi!

I made an upgrade from 16.04 LTS to 18.04.1 LTS. Everything works fine, execpt munin.

munin-cron:
```
Can't load '/usr/lib/x86_64-linux-gnu/perl5/5.26/auto/RRDs/RRDs.so' for module RRDs: /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0: undefined symbol: hb_font_funcs_set_variation_glyph_func at /usr/lib/x86_64-linux-gnu/perl/5.26/DynaLoader.pm line 187.
 at /usr/share/perl5/Munin/Master/UpdateWorker.pm line 19.
Compilation failed in require at /usr/share/perl5/Munin/Master/UpdateWorker.pm line 19.
BEGIN failed--compilation aborted at /usr/share/perl5/Munin/Master/UpdateWorker.pm line 19.
Compilation failed in require at /usr/share/perl5/Munin/Master/Update.pm line 17.
BEGIN failed--compilation aborted at /usr/share/perl5/Munin/Master/Update.pm line 17.
Compilation failed in require at /usr/share/munin/munin-update line 14.
BEGIN failed--compilation aborted at /usr/share/munin/munin-update line 14.
```

rrdtool:
```
rrdtool: symbol lookup error: /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0: undefined symbol: hb_font_funcs_set_variation_glyph_func
```

perl -MRRDs -le 'print q(ok!)':
```
Can't load '/usr/lib/x86_64-linux-gnu/perl5/5.26/auto/RRDs/RRDs.so' for module RRDs: /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0: undefined symbol: hb_font_funcs_set_variation_glyph_func at /usr/lib/x86_64-linux-gnu/perl/5.26/DynaLoader.pm line 187.
 at -e line 0.
Compilation failed in require.
BEGIN failed--compilation aborted.
```

Everything was installed via apt.
```
ii  munin                                 2.0.37-1ubuntu0.1                              all          network-wide graphing framework (grapher/gatherer)
ii  munin-common                          2.0.37-1ubuntu0.1                              all          network-wide graphing framework (common)
ii  munin-doc                             2.0.37-1ubuntu0.1                              all          network-wide graphing framework (documentation)
ii  munin-node                            2.0.37-1ubuntu0.1                              all          network-wide graphing framework (node)
ii  munin-plugins-core                    2.0.37-1ubuntu0.1                              all          network-wide graphing framework (plugins for node)
ii  munin-plugins-extra                   2.0.37-1ubuntu0.1                              all          network-wide graphing framework (user contributed plugins for node)
ii  librrd8:amd64                         1.7.0-1build1                                  amd64        time-series data storage and display system (runtime library)
ii  librrds-perl:amd64                    1.7.0-1build1                                  amd64        time-series data storage and display system (Perl interface, shared)
ii  rrdtool                               1.7.0-1build1                                  amd64        time-series data storage and display system (programs)
ii  perl                                  5.26.1-6ubuntu0.2                              amd64        Larry Wall's Practical Extraction and Report Language
ii  perl-base                             5.26.1-6ubuntu0.2                              amd64        minimal Perl system
ii  perl-modules-5.26                     5.26.1-6ubuntu0.2                              all          Core Perl modules
```

I tried to fix it for a few day, but i'm stuck. Thanks for your help!

---

### Post by hellspawn754 on 2018-09-24
i solved the problem by compiling rrdtool by myself and replaced 
/usr/lib/x86_64-linux-gnu/perl5/5.26/auto/RRDs/RRDs.so

now it works but i have no clue whats wrong with the package?!?

---

