---
title: "Ubuntu with Wine key config"
date: 2009-03-15
forum: Wine
---

### Post by 133794m3r on 2009-03-15
edit:close thread or marked as solve is not working but this thread can be now labeled as solved.

how do i get to teh reg edit in a wine i had compiled and installed by hand? as needed by this guide thing
> 
Graphical and Icon corruption:

Note that this used to be a tweak needed to boost FPS, but is apparently not needed anymore for non-ATI users.

   1. Open the registry editor and navigate to the following key

      HKEY_CURRENT_USER\Software\Wine\
   2. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
   3.

      Right-click on the wine folder and select [NEW] then [KEY]
   4.

      Replace the text New Key #1 with OpenGL
   5.

      Right-click in the right hand pane and select [NEW] then [String Value]
   6.

      Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
   7. Then double click anywhere on the line, a dialog box will open.
   8.

      In the value field type GL_ARB_vertex_buffer_object

I don't play WoW but still thought it was worth a try to increase the FPS on the games i play :/ since i'm on an ATI card. I'm playing PW which seems to not like Linux b/c of it's Directx. Also teh FPS seems to degrade after time of play for some unknown reason.

---

