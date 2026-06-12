---
title: "Including many header files in Geany"
date: 2009-06-02
forum: Ubuntu Dev Link Forum
---

### Post by Liminalitus on 2009-06-02
Hello all. I'm trying to create an app that uses a GUI with gtkmm. When I Include the header file gtkmm.h and try to compile something, I get a compiler error that says all the header files that gtkmm.h includes are missing. Is there a way to link all these files at once with Geany? I could add /usr/include/gtkmm-2.4/gtkmm in every include line in every single header file but that would take very long.

Here is what I am trying to compile (A sample program from the PDF guide):

```

#include </usr/include/gtkmm-2.4/gtkmm.h>
#include <iostream>
int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);
    Gtk::Window window;
    Gtk::Main::run(window);
    return 0;
}

```

Here are the errors I am getting (quite long):

[COLOR=Red]/usr/include/gtkmm-2.4/gtkmm.h:29:20: error: glibmm.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:30:19: error: giomm.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:31:19: error: gdkmm.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:33:26: error: gtkmm/object.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:34:31: error: gtkmm/aboutdialog.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:35:28: error: gtkmm/accelkey.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:36:30: error: gtkmm/accelgroup.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:37:30: error: gtkmm/adjustment.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:38:29: error: gtkmm/alignment.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:39:25: error: gtkmm/arrow.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:40:31: error: gtkmm/aspectframe.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:41:29: error: gtkmm/assistant.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:42:24: error: gtkmm/base.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:43:23: error: gtkmm/bin.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:44:23: error: gtkmm/box.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:45:27: error: gtkmm/builder.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:46:26: error: gtkmm/button.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:47:29: error: gtkmm/buttonbox.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:48:28: error: gtkmm/cellview.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:49:31: error: gtkmm/checkbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:50:33: error: gtkmm/checkmenuitem.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:51:32: error: gtkmm/cellrenderer.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:52:37: error: gtkmm/cellrendereraccel.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:53:37: error: gtkmm/cellrenderercombo.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:54:38: error: gtkmm/cellrendererpixbuf.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:55:40: error: gtkmm/cellrendererprogress.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:56:36: error: gtkmm/cellrendererspin.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:57:36: error: gtkmm/cellrenderertext.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:58:38: error: gtkmm/cellrenderertoggle.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:59:31: error: gtkmm/colorbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:60:34: error: gtkmm/colorselection.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:61:45: error: gtkmm/combo.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:62:28: error: gtkmm/combobox.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:63:33: error: gtkmm/comboboxentry.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:64:37: error: gtkmm/comboboxentrytext.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:65:32: error: gtkmm/comboboxtext.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:66:29: error: gtkmm/container.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:67:25: error: gtkmm/curve.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:68:26: error: gtkmm/dialog.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:69:31: error: gtkmm/drawingarea.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:70:28: error: gtkmm/editable.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:71:25: error: gtkmm/entry.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:72:28: error: gtkmm/expander.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:73:25: error: gtkmm/enums.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:74:28: error: gtkmm/eventbox.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:75:31: error: gtkmm/filechooser.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:76:37: error: gtkmm/filechooserbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:77:37: error: gtkmm/filechooserdialog.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:78:37: error: gtkmm/filechooserwidget.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:79:30: error: gtkmm/filefilter.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:80:53: error: gtkmm/fileselection.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:81:25: error: gtkmm/fixed.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:82:30: error: gtkmm/fontbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:83:33: error: gtkmm/fontselection.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:84:25: error: gtkmm/frame.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:86:29: error: gtkmm/handlebox.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:87:27: error: gtkmm/iconset.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:88:31: error: gtkmm/iconfactory.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:89:30: error: gtkmm/iconsource.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:90:29: error: gtkmm/icontheme.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:91:28: error: gtkmm/iconview.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:92:25: error: gtkmm/image.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:93:33: error: gtkmm/imagemenuitem.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:94:31: error: gtkmm/inputdialog.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:95:24: error: gtkmm/item.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:96:28: error: gtkmm/calendar.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:97:29: error: gtkmm/invisible.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:98:25: error: gtkmm/label.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:99:26: error: gtkmm/layout.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:100:29: error: gtkmm/liststore.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:101:32: error: gtkmm/listviewtext.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:102:30: error: gtkmm/linkbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:103:24: error: gtkmm/main.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:104:24: error: gtkmm/menu.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:105:30: error: gtkmm/menu_elems.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:106:27: error: gtkmm/menubar.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:107:28: error: gtkmm/menuitem.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:108:29: error: gtkmm/menushell.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:109:33: error: gtkmm/messagedialog.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:110:24: error: gtkmm/misc.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:111:28: error: gtkmm/notebook.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:113:30: error: gtkmm/optionmenu.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:114:25: error: gtkmm/paned.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:115:29: error: gtkmm/pagesetup.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:116:39: error: gtkmm/pagesetupunixdialog.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:117:29: error: gtkmm/papersize.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:118:32: error: gtkmm/printcontext.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:119:27: error: gtkmm/printer.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:120:28: error: gtkmm/printjob.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:121:34: error: gtkmm/printoperation.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:122:41: error: gtkmm/printoperationpreview.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:123:33: error: gtkmm/printsettings.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:124:35: error: gtkmm/printunixdialog.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:125:31: error: gtkmm/progressbar.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:126:31: error: gtkmm/radioaction.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:127:31: error: gtkmm/radiobutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:128:33: error: gtkmm/radiomenuitem.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:129:35: error: gtkmm/radiotoolbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:130:25: error: gtkmm/range.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:131:32: error: gtkmm/recentaction.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:132:33: error: gtkmm/recentchooser.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:133:39: error: gtkmm/recentchooserdialog.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:134:37: error: gtkmm/recentchoosermenu.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:135:39: error: gtkmm/recentchooserwidget.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:136:32: error: gtkmm/recentfilter.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:137:30: error: gtkmm/recentinfo.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:138:33: error: gtkmm/recentmanager.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:139:25: error: gtkmm/ruler.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:140:25: error: gtkmm/scale.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:141:29: error: gtkmm/scrollbar.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:142:34: error: gtkmm/scrolledwindow.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:143:29: error: gtkmm/separator.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:144:37: error: gtkmm/separatormenuitem.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:145:37: error: gtkmm/separatortoolitem.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:146:28: error: gtkmm/settings.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:147:29: error: gtkmm/sizegroup.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:148:30: error: gtkmm/spinbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:149:29: error: gtkmm/statusbar.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:150:30: error: gtkmm/statusicon.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:151:25: error: gtkmm/stock.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:152:27: error: gtkmm/stockid.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:153:29: error: gtkmm/stockitem.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:154:25: error: gtkmm/style.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:155:25: error: gtkmm/table.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:156:35: error: gtkmm/tearoffmenuitem.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:157:30: error: gtkmm/textbuffer.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:158:35: error: gtkmm/textchildanchor.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:159:28: error: gtkmm/textiter.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:160:28: error: gtkmm/textmark.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:161:27: error: gtkmm/texttag.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:162:32: error: gtkmm/texttagtable.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:163:28: error: gtkmm/textview.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:164:32: error: gtkmm/toggleaction.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:165:32: error: gtkmm/togglebutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:166:27: error: gtkmm/toolbar.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:167:28: error: gtkmm/toolitem.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:168:30: error: gtkmm/toolbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:169:36: error: gtkmm/toggletoolbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:170:34: error: gtkmm/menutoolbutton.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:171:27: error: gtkmm/tooltip.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:172:28: error: gtkmm/tooltips.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:173:29: error: gtkmm/treemodel.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:174:35: error: gtkmm/treemodelfilter.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:175:33: error: gtkmm/treemodelsort.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:176:28: error: gtkmm/treepath.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:177:36: error: gtkmm/treerowreference.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:178:33: error: gtkmm/treeselection.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:179:29: error: gtkmm/treestore.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:180:28: error: gtkmm/treeview.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:181:34: error: gtkmm/treeviewcolumn.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:182:29: error: gtkmm/uimanager.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:183:28: error: gtkmm/viewport.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:184:26: error: gtkmm/widget.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:185:26: error: gtkmm/window.h: No such file or directory
twin.cpp: In function &#8216;int main(int, char**)&#8217;:
twin.cpp:5: error: &#8216;Gtk&#8217; has not been declared
twin.cpp:5: error: expected `;' before &#8216;kit&#8217;
twin.cpp:6: error: &#8216;Gtk&#8217; has not been declared
twin.cpp:6: error: expected `;' before &#8216;window&#8217;
twin.cpp:7: error: &#8216;Gtk&#8217; has not been declared
twin.cpp:7: error: &#8216;window&#8217; was not declared in this scope
[/COLOR]

---

### Post by johnl on 2009-06-03
```

#include </usr/include/gtkmm-2.4/gtkmm.h>

```

Is causing the problem.  You should use:

```

#include <gtkmm.h>

```

and pass the following to gcc:  `pkg-config --cflags gtkmm-2.4`

This will add the necessary -I statements (include directories) to the gcc CLI.

You will also need to pass `pkg-config --libs gtkmm-2.4` when linking.


Hope this helps.

---

