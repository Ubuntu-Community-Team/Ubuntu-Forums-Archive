---
title: "World of Tanks Wine Patch"
date: 2010-08-01
forum: Wine
---

### Post by arewethereyet on 2010-08-01
Greetings.

I have come across a patch I need to install to get the mouse working in this game. I would be grateful if someone could explain how I would apply this patch to wine.

Wine: 1.2
Patch File name: wine-1.2-wot2.diff

```
diff -pur wine-1.2/dlls/user32/Makefile.in wine-1.2-wot//dlls/user32/Makefile.in
--- wine-1.2/dlls/user32/Makefile.in    2010-07-16 19:05:45.000000000 +0400
+++ wine-1.2-wot//dlls/user32/Makefile.in    2010-07-18 16:21:44.000000000 +0400
@@ -5,7 +5,7 @@ SRCDIR    = @srcdir@
 VPATH     = @srcdir@
 MODULE    = user32.dll
 IMPORTLIB = user32
-IMPORTS   = gdi32 advapi32 kernel32 ntdll
+IMPORTS   = gdi32 advapi32 kernel32 ntdll dinput8 dinput dxguid
 DELAYIMPORTS = imm32
 
 C_SRCS = \
diff -pur wine-1.2/dlls/user32/input.c wine-1.2-wot//dlls/user32/input.c
--- wine-1.2/dlls/user32/input.c    2010-07-16 19:05:45.000000000 +0400
+++ wine-1.2-wot//dlls/user32/input.c    2010-07-18 16:21:44.000000000 +0400
@@ -22,6 +22,14 @@
  * Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301, USA
  */
 
+/*
+ * Modififed by Reco 2009
+ * patch is based on 
+ * http://win2kgaming.site90.com/phpBB2/viewtopic.php?f=6&t=7
+ * OldCigarettes Windows 2000 XP API Wrapper Pack 
+ * Released under LGPL       
+ */
+
 #include "config.h"
 #include "wine/port.h"
 
@@ -46,10 +54,59 @@
 #include "wine/server.h"
 #include "wine/debug.h"
 #include "wine/unicode.h"
+#include "dinput.h"
 
+DWORD WINAPI __pollInput(HWND) ;
 WINE_DEFAULT_DEBUG_CHANNEL(win);
 WINE_DECLARE_DEBUG_CHANNEL(keyboard);
 
+BOOL                    mouse_init = FALSE;
+BOOL                    first_raw  = TRUE;
+LPDIRECTINPUT8A         lpdi;
+LPDIRECTINPUTDEVICE8A   m_mouse;
+
+static DIMOUSESTATE2 mouse_state;
+static DIMOUSESTATE2 mouse_state_prev;
+
+DWORD winCenterX, winCenterY;
+DWORD winX, winY;
+DWORD winR, winB;
+LONG prevX, prevY;
+#define arL 20
+struct hist_data {
+  DWORD val;
+  int cnt;
+};
+int cntY1, cntY2;
+
+int prevCenterY = 0;
+int wot_snipe = 0;
+
+#define MOUSE_INPUT          0xABC123
+#define RIM_TYPEMOUSE        0
+#define RIM_INPUT          0x00000000
+#define MOUSE_MOVE_RELATIVE      0x00000000
+#define MOUSE_MOVE_ABSOLUTE      0x00000001
+#define MOUSE_VIRTUAL_DESKTOP     0x00000002
+#define RI_MOUSE_LEFT_BUTTON_DOWN  0x0001
+#define RI_MOUSE_LEFT_BUTTON_UP    0x0002
+#define RI_MOUSE_RIGHT_BUTTON_DOWN 0x0004
+#define RI_MOUSE_RIGHT_BUTTON_UP 0x0008
+#define RI_MOUSE_MIDDLE_BUTTON_DOWN  0x0010
+#define RI_MOUSE_MIDDLE_BUTTON_UP  0x0020
+#define RI_MOUSE_BUTTON_1_DOWN     RI_MOUSE_LEFT_BUTTON_DOWN
+#define RI_MOUSE_BUTTON_1_UP   RI_MOUSE_LEFT_BUTTON_UP
+#define RI_MOUSE_BUTTON_2_DOWN   RI_MOUSE_RIGHT_BUTTON_DOWN
+#define RI_MOUSE_BUTTON_2_UP   RI_MOUSE_RIGHT_BUTTON_UP
+#define RI_MOUSE_BUTTON_3_DOWN   RI_MOUSE_MIDDLE_BUTTON_DOWN
+#define RI_MOUSE_BUTTON_3_UP   RI_MOUSE_MIDDLE_BUTTON_UP
+#define RI_MOUSE_BUTTON_4_DOWN   0x0040
+#define RI_MOUSE_BUTTON_4_UP   0x0080
+#define RI_MOUSE_BUTTON_5_DOWN   0x0100
+#define RI_MOUSE_BUTTON_5_UP   0x0200
+#define RI_MOUSE_WHEEL       0x0400
+#define RIDEV_INPUTSINK        0x00000100
+#define MOUSE_DEVICE_HANDLE      0x1337
 
 /***********************************************************************
  *           get_key_state
@@ -384,10 +441,82 @@ UINT WINAPI GetRawInputDeviceList(PRAWIN
 /******************************************************************
 *        RegisterRawInputDevices (USER32.@)
 */
-BOOL WINAPI DECLSPEC_HOTPATCH RegisterRawInputDevices(PRAWINPUTDEVICE pRawInputDevices, UINT uiNumDevices, UINT cbSize)
+BOOL WINAPI RegisterRawInputDevices(PRAWINPUTDEVICE pRawInputDevices, UINT uiNumDevices, UINT cbSize)
 {
-    FIXME("(pRawInputDevices=%p, uiNumDevices=%d, cbSize=%d) stub!\n", pRawInputDevices, uiNumDevices, cbSize);
+    DWORD flags;
+    HWND hWnd;
+
+    RECT rect;
+
+    if(first_raw) {
+      FIXME("(pRawInputDevices=%p, uiNumDevices=%d, cbSize=%d) stub!\n", pRawInputDevices, uiNumDevices, cbSize);
+      first_raw = FALSE;
+      return TRUE;
+    }
+
+    WARN("Only mouse is supported.\n");
+    if(uiNumDevices != 1) 
+   return FALSE;
+    if(pRawInputDevices->usUsagePage != 0x01 || pRawInputDevices->usUsage != 0x02) 
+   return FALSE;
+
+    TRACE("Get the window handle if we need to...\n");
+    hWnd = pRawInputDevices->hwndTarget;
+    if(!hWnd) hWnd = GetActiveWindow();
+    if(!hWnd) return FALSE;
+
+ if(!GetWindowRect(hWnd, &rect))
+   return FALSE;
+ winCenterX = (rect.right  - rect.left) / 2;
+ winCenterY = (rect.bottom - rect.top ) / 2;
+ winX = rect.left;
+ winY = rect.top ;
+ winR = rect.right;
+ winB = rect.bottom ;
+
+    TRACE("Trying to map flags to DirectX...\n");
+    flags = 0;
+    if(pRawInputDevices->dwFlags & RIDEV_INPUTSINK) 
+   flags |= DISCL_BACKGROUND;
+    else
+   flags |= DISCL_FOREGROUND;
+    flags |= DISCL_NONEXCLUSIVE;
+
+    TRACE("Init mouse\n");
+    if (FAILED(DirectInput8Create(GetModuleHandleW(NULL), 
+     DIRECTINPUT_VERSION, &IID_IDirectInput8W, (void**)&lpdi, NULL))) 
+ {
+   ERR("DirectInput8Create failed.\n");
+        return FALSE;
+ }
+
+    if (FAILED(lpdi->lpVtbl->CreateDevice(lpdi, &GUID_SysMouse, &m_mouse, NULL)))
+ {
+   ERR("CreateDevice failed.\n");
+        return FALSE;
+ }
+
+    if (FAILED(m_mouse->lpVtbl->SetCooperativeLevel(m_mouse, hWnd, flags)))
+ {
+   ERR("SetCooperativeLevel failed.\n");
+        return FALSE;
+ }
+
+    if (FAILED(m_mouse->lpVtbl->SetDataFormat(m_mouse, &c_dfDIMouse2)))
+ {
+   ERR("SetDataFormat failed.\n");
+        return FALSE;
+ }
 
+    m_mouse->lpVtbl->Acquire(m_mouse); //OK if we don't acquire now
+
+    if(!CreateThread(NULL, 0, __pollInput, hWnd, 0, NULL))
+ {
+   ERR("Failed to CreateThread for __pollInput.\n");
+        return FALSE;
+ }
+
+    mouse_init = TRUE;
     return TRUE;
 }
 
@@ -397,12 +526,116 @@ BOOL WINAPI DECLSPEC_HOTPATCH RegisterRa
 */
 UINT WINAPI GetRawInputData(HRAWINPUT hRawInput, UINT uiCommand, LPVOID pData, PUINT pcbSize, UINT cbSizeHeader)
 {
-    FIXME("(hRawInput=%p, uiCommand=%d, pData=%p, pcbSize=%p, cbSizeHeader=%d) stub!\n",
-            hRawInput, uiCommand, pData, pcbSize, cbSizeHeader);
+    HRESULT hr;
+    RAWINPUT *raw;
+    POINT pos;
+    int i,j,cnt_max;
+    HWND hWnd;
+    RECT rect;
+    int diffY;
 
-    return 0;
-}
+    if(pData == NULL) 
+    {
+        *pcbSize = sizeof(RAWINPUT);
+        return 0;
+    }
+
+    raw = (RAWINPUT *)pData;
+    if(!mouse_init) return FALSE;
+
+    raw->header.dwType = RIM_TYPEMOUSE;
+    raw->header.dwSize = sizeof(RAWINPUT);
+    raw->header.hDevice = MOUSE_DEVICE_HANDLE;
+    raw->header.wParam = RIM_INPUT;
+
+    hr = m_mouse->lpVtbl->GetDeviceState(m_mouse, sizeof(DIMOUSESTATE2), (LPVOID)&mouse_state);
+    if(FAILED(hr)) 
+    {
+      TRACE("Re-acquiring input.\n");
+      m_mouse->lpVtbl->Acquire(m_mouse);
+      while(hr == DIERR_INPUTLOST) 
+      {
+        hr = m_mouse->lpVtbl->Acquire(m_mouse);
+      }
+      if(FAILED(hr)) 
+      {
+        TRACE("Mouse re-acquire failed.\n");
+        return 0;
+      }
+      m_mouse->lpVtbl->GetDeviceState(m_mouse, sizeof(DIMOUSESTATE2), (LPVOID)&mouse_state);
+    }
 
+    GetCursorPos(&pos);
+    if(!hWnd) hWnd = GetActiveWindow();
+    if(!GetWindowRect(hWnd, &rect)) return FALSE;
+ winCenterX = (rect.right  - rect.left) / 2;                                                                                                                                         
+ winCenterY = (rect.bottom - rect.top ) / 2;                                                                                                                                         
+ winX = rect.left;
+ winY = rect.top ;
+ winR = rect.right;
+ winB = rect.bottom;
+
+////////////////Quite ugly World of Tanks-related hack///////////////////////
+    if ((abs(pos.y-prevY-0.15*winCenterY)<2)&&(abs(pos.x-prevX)<0.01*winCenterX)&&(!wot_snipe)) wot_snipe = 1;
+    else if ((abs(prevY-pos.y-0.15*winCenterY)<2)&&(abs(pos.x-prevX)<0.01*winCenterX)&&(wot_snipe)) wot_snipe = 0;
+
+    if (!wot_snipe) diffY = round(0.15*winCenterY); // in WoT in normal mode ordinate of position deviates slightly
+    else diffY = 0;    // in sniping/howitzer mode it's ok, no diff needed
+
+    FIXME("PrevY %d, posy %d, diffY %d, snipe %d\n", prevY, pos.y, diffY, wot_snipe);
+/////////////////////////////////////////////////////////////////////////////
+
+
+
+    raw->data.mouse.usFlags = MOUSE_MOVE_RELATIVE;
+    raw->data.mouse.lLastX = pos.x - winCenterX;
+    raw->data.mouse.lLastY = pos.y - winCenterY + diffY;
+
+    raw->data.mouse.usButtonData = mouse_state.lZ & 0xffff;
+    raw->data.mouse.usButtonFlags = 0;
+    raw->data.mouse.ulRawButtons = 0;
+
+    if(raw->data.mouse.usButtonData != 0) raw->data.mouse.usButtonFlags |= RI_MOUSE_WHEEL;
+
+    for(i = 0; i < 8; i++) 
+        if(mouse_state.rgbButtons[i] & 0x80) 
+            raw->data.mouse.ulRawButtons |= 1<<i;
+
+    if(mouse_state.rgbButtons[0] & 0x80 && !(mouse_state_prev.rgbButtons[0] & 0x80))
+        raw->data.mouse.usButtonFlags |= RI_MOUSE_LEFT_BUTTON_DOWN;
+
+    if(!(mouse_state.rgbButtons[0] & 0x80) && mouse_state_prev.rgbButtons[0] & 0x80)
+        raw->data.mouse.usButtonFlags |= RI_MOUSE_LEFT_BUTTON_UP;
+
+    if(mouse_state.rgbButtons[1] & 0x80 && !(mouse_state_prev.rgbButtons[1] & 0x80))
+        raw->data.mouse.usButtonFlags |= RI_MOUSE_RIGHT_BUTTON_DOWN;
+
+    if(!(mouse_state.rgbButtons[1] & 0x80) && mouse_state_prev.rgbButtons[1] & 0x80)
+        raw->data.mouse.usButtonFlags |= RI_MOUSE_RIGHT_BUTTON_UP;
+
+    if(!(mouse_state.rgbButtons[2] & 0x80) && mouse_state_prev.rgbButtons[2] & 0x80)
+        raw->data.mouse.usButtonFlags |= RI_MOUSE_MIDDLE_BUTTON_UP;
+
+    if(mouse_state.rgbButtons[3] & 0x80 && !(mouse_state_prev.rgbButtons[3] & 0x80))
+        raw->data.mouse.usButtonFlags |= RI_MOUSE_BUTTON_4_DOWN;
+
+    if(!(mouse_state.rgbButtons[3] & 0x80) && mouse_state_prev.rgbButtons[3] & 0x80)
+        raw->data.mouse.usButtonFlags |= RI_MOUSE_BUTTON_4_UP;
+
+ if(mouse_state.rgbButtons[4] & 0x80 && !(mouse_state_prev.rgbButtons[4] & 0x80))
+        raw->data.mouse.usButtonFlags |= RI_MOUSE_BUTTON_5_DOWN;
+
+    if(!(mouse_state.rgbButtons[4] & 0x80) && mouse_state_prev.rgbButtons[4] & 0x80)
+        raw->data.mouse.usButtonFlags |= RI_MOUSE_BUTTON_5_UP;
+
+    memcpy(&mouse_state_prev, &mouse_state, sizeof(DIMOUSESTATE2));
+    prevX = pos.x;
+    prevY = pos.y;
+    prevCenterY = winCenterY;
+
+    return sizeof(RAWINPUT);
+
+}
 
 /******************************************************************
 *        GetRawInputBuffer (USER32.@)
@@ -436,15 +669,88 @@ UINT WINAPI GetRawInputDeviceInfoW(HANDL
     return 0;
 }
 
+DWORD WINAPI __pollInput(HWND hWnd)                                                                                                                                                  
+{                                                                                                                                                                                    
+    for(;;)                                                                                                                                                                          
+ {                                                                                                                                                                                   
+        Sleep(1000/60);                                                                                                                                                              
+   TRACE("SendMessageW(%p,%p,%p,%p)\n", hWnd, WM_INPUT, RIM_INPUT, MOUSE_INPUT);                                                                                                     
+        SendMessageW(hWnd, WM_INPUT, RIM_INPUT, MOUSE_INPUT);                                                                                                                        
+    }                                                                                                                                                                                
+    return 0;                                                                                                                                                                        
+}
 
 /******************************************************************
 *        GetRegisteredRawInputDevices (USER32.@)
 */
 UINT WINAPI GetRegisteredRawInputDevices(PRAWINPUTDEVICE pRawInputDevices, PUINT puiNumDevices, UINT cbSize)
 {
-    FIXME("(pRawInputDevices=%p, puiNumDevices=%p, cbSize=%d) stub!\n", pRawInputDevices, puiNumDevices, cbSize);
-
-    return 0;
+    DWORD flags;                                                                                                                                                                     
+    HWND hWnd;                                                                                                                                                                       
+                                                                                                                                                                                     
+    RECT rect;                                                                                                                                                                       
+                                                                                                                                                                                     
+    if(mouse_init) return 0;                                                                                                                                                         
+                                                                                                                                                                                     
+    WARN("Only mouse is supported.\n");                                                                                                                                              
+    if(puiNumDevices != 1)                                                                                                                                                           
+   return FALSE;                                                                                                                                                                     
+    if(pRawInputDevices->usUsagePage != 0x01 || pRawInputDevices->usUsage != 0x02)                                                                                                   
+   return FALSE;                                                                                                                                                                     
+                                                                                                                                                                                     
+    TRACE("Get the window handle if we need to...\n");                                                                                                                               
+    hWnd = pRawInputDevices->hwndTarget;                                                                                                                                             
+    if(!hWnd) hWnd = GetActiveWindow();                                                                                                                                              
+    if(!hWnd) return FALSE;                                                                                                                                                          
+                                                                                                                                                                                     
+ if(!GetWindowRect(hWnd, &rect))                                                                                                                                                     
+   return FALSE;                                                                                                                                                                     
+ winCenterX = (rect.right  - rect.left) / 2;                                                                                                                                         
+ winCenterY = (rect.bottom - rect.top ) / 2;                                                                                                                                         
+                                                                                                                                                                                     
+    TRACE("Trying to map flags to DirectX...\n");                                                                                                                                    
+    flags = 0;                                                                                                                                                                       
+    if(pRawInputDevices->dwFlags & RIDEV_INPUTSINK)                                                                                                                                  
+   flags |= DISCL_BACKGROUND;                                                                                                                                                        
+    else                                                                                                                                                                             
+   flags |= DISCL_FOREGROUND;                                                                                                                                                        
+    flags |= DISCL_NONEXCLUSIVE;                                                                                                                                                     
+                                                                                                                                                                                      
+    TRACE("Init mouse\n");                                                                                                                                                           
+    if (FAILED(DirectInput8Create(GetModuleHandleW(NULL),                                                                                                                            
+     DIRECTINPUT_VERSION, &IID_IDirectInput8W, (void**)&lpdi, NULL)))                                                                                                                
+ {                                                                                                                                                                                   
+   ERR("DirectInput8Create failed.\n");                                                                                                                                              
+        return FALSE;                                                                                                                                                                
+ }                                                                                                                                                                                   
+                                                                                                                                                                                     
+    if (FAILED(lpdi->lpVtbl->CreateDevice(lpdi, &GUID_SysMouse, &m_mouse, NULL)))                                                                                                    
+ {                                                                                                                                                                                   
+   ERR("CreateDevice failed.\n");                                                                                                                                                    
+        return FALSE;                                                                                                                                                                
+ }                                                                                                                                                                                   
+                                                                                                                                                                                     
+    if (FAILED(m_mouse->lpVtbl->SetCooperativeLevel(m_mouse, hWnd, flags)))
+ {                                                                                                                                                                                   
+   ERR("SetCooperativeLevel failed.\n");                                                                                                                                             
+        return FALSE;                                                                                                                                                                
+ }                                                                                                                                                                                   
+                                                                                                                                                                                     
+    if (FAILED(m_mouse->lpVtbl->SetDataFormat(m_mouse, &c_dfDIMouse2)))                                                                                                              
+ {                                                                                                                                                                                   
+   ERR("SetDataFormat failed.\n");                                                                                                                                                   
+        return FALSE;                                                                                                                                                                
+ }                                                                                                                                                                                   
+                                                                                                                                                                                     
+    m_mouse->lpVtbl->Acquire(m_mouse); //OK if we don't acquire now                                                                                                                  
+                                                                                                                                                                                     
+    if(!CreateThread(NULL, 0, __pollInput, hWnd, 0, NULL))                                                                                                                           
+ {                                                                                                                                                                                   
+   ERR("Failed to CreateThread for __pollInput.\n");                                                                                                                                 
+        return FALSE;                                                                                                                                                                
+ }                                                                                                                                                                                   
+                                                                                                                                                                                     
+    mouse_init = TRUE;
 }
 
 
diff -pur wine-1.2/dlls/winex11.drv/mouse.c wine-1.2-wot//dlls/winex11.drv/mouse.c
--- wine-1.2/dlls/winex11.drv/mouse.c    2010-07-16 19:05:45.000000000 +0400
+++ wine-1.2-wot//dlls/winex11.drv/mouse.c    2010-07-18 17:22:18.000000000 +0400
@@ -44,7 +44,7 @@ MAKE_FUNCPTR(XcursorImageLoadCursor);
 #include "wine/server.h"
 #include "wine/library.h"
 #include "wine/debug.h"
-
+#include <X11/cursorfont.h>
 WINE_DEFAULT_DEBUG_CHANNEL(cursor);
 
 /**********************************************************************/
@@ -201,17 +201,27 @@ void set_window_cursor( HWND hwnd, HCURS
 {
     struct x11drv_win_data *data;
     Cursor cursor, prev;
-
+    char *hwgl;
     if (!(data = X11DRV_get_win_data( hwnd ))) return;
-
+    hwgl = getenv("WINE_CURSOR");
     wine_tsx11_lock();
     if (!handle) cursor = get_empty_cursor();
     else if (!cursor_context || XFindContext( gdi_display, (XID)handle, cursor_context, (char **)&cursor ))
     {
         /* try to create it */
         wine_tsx11_unlock();
-        if (!(cursor = create_cursor( handle ))) return;
-
+        //if (!(cursor = create_cursor( handle ))) return;
+    //if (hwgl != NULL) cursor = XCreateFontCursor(gdi_display, XC_dotbox);
+    if (hwgl != NULL && (strcmp(hwgl, "X") == 0 || strcmp(hwgl, "XNOJIG") == 0) )  {
+        if (!(cursor = XCreateFontCursor(gdi_display, XC_left_ptr))) return;
+    }
+    else if (hwgl != NULL) {
+        if (!(cursor = XCreateFontCursor(gdi_display, XC_dotbox))) return;
+    }
+    else
+    {
+        if (!(cursor = create_cursor( handle ))) return;
+    }
         wine_tsx11_lock();
         if (!cursor_context) cursor_context = XUniqueContext();
         if (!XFindContext( gdi_display, (XID)handle, cursor_context, (char **)&prev ))
@@ -895,12 +905,56 @@ void X11DRV_ButtonPress( HWND hwnd, XEve
     int buttonNum = event->button - 1;
     WORD wData = 0;
     POINT pt;
+    
+    Pixmap blank;
+    XColor dummy;
+    char no_data[1] = {0};
+    Cursor cursor;
 
+    char *hwgl;
+    hwgl = getenv("WINE_CURSOR");
+    
     if (buttonNum >= NB_BUTTONS) return;
     if (!hwnd) return;
 
     switch (buttonNum)
     {
+    case 0:
+        if (hwgl != NULL && strcmp(hwgl,"X") > 0 ) {
+    //printf("Case 2\n");
+    wine_tsx11_lock();
+    XUndefineCursor(event->display, event->window);
+    blank = XCreateBitmapFromData (event->display, event->window, no_data, 1, 1);
+    if(blank == None)
+        WINE_FIXME("Out of memory.\n");
+    cursor = XCreatePixmapCursor(event->display, blank, blank, &dummy, &dummy, 0, 0);
+    XFreePixmap (event->display, blank);
+    XDefineCursor(event->display, event->window, cursor);
+    if (event->window)
+    {
+            XFlush( event->display);
+    }
+    wine_tsx11_unlock();
+    }
+    break;
+    case 2:
+        if (hwgl != NULL && strcmp(hwgl,"X") > 0 ) {
+    //printf("Case 2\n");
+    wine_tsx11_lock();
+    XUndefineCursor(event->display, event->window);
+    blank = XCreateBitmapFromData (event->display, event->window, no_data, 1, 1);
+    if(blank == None)
+        WINE_FIXME("Out of memory.\n");
+    cursor = XCreatePixmapCursor(event->display, blank, blank, &dummy, &dummy, 0, 0);
+    XFreePixmap (event->display, blank);
+    XDefineCursor(event->display, event->window, cursor);
+    if (event->window)
+    {
+            XFlush( event->display);
+    }
+    wine_tsx11_unlock();
+    }
+    break;
     case 3:
         wData = WHEEL_DELTA;
         break;
@@ -938,12 +992,38 @@ void X11DRV_ButtonRelease( HWND hwnd, XE
     int buttonNum = event->button - 1;
     WORD wData = 0;
     POINT pt;
+    
+    char *hwgl;
+    hwgl = getenv("WINE_CURSOR");
 
     if (buttonNum >= NB_BUTTONS || !button_up_flags[buttonNum]) return;
     if (!hwnd) return;
 
     switch (buttonNum)
     {
+    case 0:
+
+        if (hwgl != NULL && strcmp(hwgl,"X") > 0 ) {
+    wine_tsx11_lock();
+    XUndefineCursor(event->display, event->window);
+    if (event->window)
+    {
+            XFlush( event->display );
+    }
+    wine_tsx11_unlock();
+    }
+    break;
+    case 2:
+        if (hwgl != NULL && strcmp(hwgl,"X") > 0 ) {
+    wine_tsx11_lock();
+    XUndefineCursor(event->display, event->window);
+    if (event->window)
+    {
+            XFlush( event->display );
+    }
+    wine_tsx11_unlock();
+    }
+    break;
     case 5:
         wData = XBUTTON1;
         break;
diff -pur wine-1.2/include/winuser.h wine-1.2-wot//include/winuser.h
--- wine-1.2/include/winuser.h    2010-07-16 19:05:45.000000000 +0400
+++ wine-1.2-wot//include/winuser.h    2010-07-18 16:21:44.000000000 +0400
@@ -491,8 +491,8 @@ typedef struct tagRAWMOUSE {
         struct {
             USHORT usButtonFlags;
             USHORT usButtonData;
-        } DUMMYSTRUCTNAME;
-    } DUMMYUNIONNAME;
+        };
+    };
     ULONG ulRawButtons;
     LONG  lLastX;
     LONG  lLastY;

```

From what I understand I would have to download the wine installation itself, the somehow apply this patch to it, then install the new wine package after wiping the old one?

Thank you in advance for any help!

---

### Post by hikaricore on 2010-08-01
You actually need to download the source for wine.
Patch the source.
Compile the source.
Then install the compiled source.

There are plenty of guides around the internet on how to patch and compile wine from source.
Making sure you've removed any other wine installations beforehand to avoid conflicts.

---

### Post by arewethereyet on 2010-08-02
Thank you for the response. i got everything worked out :D

---

### Post by _DM_ on 2010-08-22
Getting failes on patching... what am I doing wrong?

```
patch -p1 < wine-1.2-wot2.diff
```

```
(Stripping trailing CRs from patch.)
patching file Makefile.in
Hunk #1 FAILED at 5.
1 out of 1 hunk FAILED -- saving rejects to file Makefile.in.rej
(Stripping trailing CRs from patch.)
patching file input.c
Hunk #1 FAILED at 22.
Hunk #2 FAILED at 46.
Hunk #3 FAILED at 384.
Hunk #4 FAILED at 397.
Hunk #5 FAILED at 436.
5 out of 5 hunks FAILED -- saving rejects to file input.c.rej
(Stripping trailing CRs from patch.)
patching file mouse.c
Hunk #1 FAILED at 44.
Hunk #2 FAILED at 201.
Hunk #3 FAILED at 895.
Hunk #4 FAILED at 938.
4 out of 4 hunks FAILED -- saving rejects to file mouse.c.rej
(Stripping trailing CRs from patch.)
patching file winuser.h
patch unexpectedly ends in middle of line
Hunk #1 FAILED at 491.
1 out of 1 hunk FAILED -- saving rejects to file winuser.h.rej
```

---

### Post by thisguy123 on 2011-06-05
> **hikaricore said:**
> You actually need to download the source for wine.
Patch the source.
Compile the source.
Then install the compiled source.

There are plenty of guides around the internet on how to patch and compile wine from source.
Making sure you've removed any other wine installations beforehand to avoid conflicts. :confused: Im tired of this every where I go Im a lurker I never post but Im sick of this answer from people that sit on forums trying to get post counts all day(you excluded because your a developer) " first get the source then compile it with the patch then install"<-how..... "there's plenty o TuT's on the net"<- link or gtfo

!please if your going to posts things like this have step by step directions or a link where to find them!" its like telling a person thats never driven a car to just get in and drive its not teaching them anything.......and I would gladly RTFM if some 1 could point me to a manual.     ./run_flame_endscript.sh

p.s. sorry for the frustration

---

### Post by johnnynoone on 2011-10-15
In the comments section of that patch:
```
+/*
+ * Modififed by Reco 2009
+ * patch is based on 
+ * http://win2kgaming.site90.com/phpBB2/viewtopic.php?f=6&t=7
+ * OldCigarettes Windows 2000 XP API Wrapper Pack 
+ * Released under LGPL       
+ */
```
As the win2kgaming forums have moved, you can find that thread referenced here:
[http://oldcigaret.info/win2k/phpBB3/viewtopic.php?f=6&t=7](http://oldcigaret.info/win2k/phpBB3/viewtopic.php?f=6&t=7)

---

