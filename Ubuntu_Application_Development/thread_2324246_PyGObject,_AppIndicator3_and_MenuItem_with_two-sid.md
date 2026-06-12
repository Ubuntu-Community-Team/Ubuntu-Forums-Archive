---
title: "PyGObject, AppIndicator3 and MenuItem with two-sided label"
date: 2016-05-12
forum: Ubuntu Application Development
---

### Post by benjamindean on 2016-05-12
I'm stuck with that problem for two weeks already and it seems like Unity panel is ignoring any kind of markup in it's indicators. 
I'm using Gtk.Builder() to build an AppIndicator's menu. The goal is to have a MenuItem with two labels inside it (one on the left and one on the right), but for some reason, the second label gets ignored and only the first one is rendered correctly. I'm pretty certain its possible, because Calendar widget on Ubuntu have the same kind of MenuItem in it (in Appointments and Timezone sections).

```

[COLOR=#7D2727]<interface>[/COLOR][COLOR=#303336]
    [/COLOR][COLOR=#7D2727]<requires[/COLOR][COLOR=#E64320]lib[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"gtk+"[/COLOR][COLOR=#E64320]version[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"3.12"[/COLOR][COLOR=#7D2727]/>[/COLOR][COLOR=#303336]
    [/COLOR][COLOR=#858C93]<!-- interface-naming-policy project-wide -->[/COLOR][COLOR=#303336]
    [/COLOR][COLOR=#7D2727]<object[/COLOR][COLOR=#E64320]class[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"GtkMenu"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]
        [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"visible"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]True[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
        [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"can_focus"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]False[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
        [/COLOR][COLOR=#7D2727]<child>[/COLOR][COLOR=#303336]
            [/COLOR][COLOR=#7D2727]<object[/COLOR][COLOR=#E64320]class[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"GtkMenuItem"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]
                [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"visible"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]True[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                [/COLOR][COLOR=#7D2727]<child>[/COLOR][COLOR=#303336]
                    [/COLOR][COLOR=#7D2727]<object[/COLOR][COLOR=#E64320]class[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"GtkBox"[/COLOR][COLOR=#E64320]id[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"box"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]
                        [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"visible"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]True[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                        [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"can_focus"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]False[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                        [/COLOR][COLOR=#7D2727]<child>[/COLOR][COLOR=#303336]
                            [/COLOR][COLOR=#7D2727]<object[/COLOR][COLOR=#E64320]class[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"GtkLabel"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]
                                [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"visible"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]True[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                                [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"label"[/COLOR][COLOR=#E64320]translatable[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"yes"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]Label 1[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                                [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"use_underline"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]True[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                                [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"halign"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]start[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                            [/COLOR][COLOR=#7D2727]</object>[/COLOR][COLOR=#303336]
                        [/COLOR][COLOR=#7D2727]</child>[/COLOR][COLOR=#303336]
                        [/COLOR][COLOR=#7D2727]<child>[/COLOR][COLOR=#303336]
                            [/COLOR][COLOR=#7D2727]<object[/COLOR][COLOR=#E64320]class[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"GtkLabel"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]
                                [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"visible"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]True[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                                [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"label"[/COLOR][COLOR=#E64320]translatable[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"yes"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]Label 2[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                                [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"use_underline"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]True[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                                [/COLOR][COLOR=#7D2727]<property[/COLOR][COLOR=#E64320]name[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#0F74BD]"halign"[/COLOR][COLOR=#7D2727]>[/COLOR][COLOR=#303336]end[/COLOR][COLOR=#7D2727]</property>[/COLOR][COLOR=#303336]
                            [/COLOR][COLOR=#7D2727]</object>[/COLOR][COLOR=#303336]
                        [/COLOR][COLOR=#7D2727]</child>[/COLOR][COLOR=#303336]
                    [/COLOR][COLOR=#7D2727]</object>[/COLOR][COLOR=#303336]
                [/COLOR][COLOR=#7D2727]</child>[/COLOR][COLOR=#303336]
            [/COLOR][COLOR=#7D2727]</object>[/COLOR][COLOR=#303336]
        [/COLOR][COLOR=#7D2727]</child>[/COLOR][COLOR=#303336]
    [/COLOR][COLOR=#7D2727]</object>[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#7D2727]</interface>
[/COLOR]
```[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So far, I tried:

1. set_markup method on a label with various markup approaches. 
2. HBox packing.
3. Many other things, like using Label with Mnemonic and so on.

Am I missing something? Thanks in advance![/FONT][/COLOR]

---

