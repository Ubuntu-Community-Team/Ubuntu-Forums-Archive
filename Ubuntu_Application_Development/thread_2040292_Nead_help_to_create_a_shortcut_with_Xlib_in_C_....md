---
title: "Nead help to create a shortcut with Xlib in C ..."
date: 2012-08-10
forum: Ubuntu Application Development
---

### Post by didjoman on 2012-08-10
Hello,
I am creating a sort of window manager in bash and in C and I would like to create shortcuts for my application with the Xlib, but I have some troubles to do it ... 

I need to make 2 different shortcuts : 

SUPER + ALT_L + letter
SUPER + letter

The first one functions when I type SUPER, then Alt and finally the letter. But it doesn't functions when I begin by typing ALT_L .... 
And the 2° doesn't functions ... 

I don't really know what to do ... 
Could you help me ? 
(please, sorry for the possible mistakes in English, I am french)  

Here is what I have done : 
```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <X11/Xlib.h>

GC gc; // Contexte graphique
Display* display;
int screen;
Window root;

void swallow_keystroke(Display * dpy, XEvent * ev)
{
  XAllowEvents(dpy, AsyncKeyboard, ev->xkey.time);
}

void passthru_keystroke(Display * dpy, XEvent * ev)
{
  /* pass it through to the app, as if we never intercepted it */
  XAllowEvents(dpy, ReplayKeyboard, ev->xkey.time);
  XFlush(dpy); 
}


int main(int argc, char* argv[]){

  char cwd[1024];
  getcwd(cwd, sizeof(cwd));

  // Connexion à un serveur X
  display = XOpenDisplay(NULL);
  if(!display){
    printf("Can not open display.\n");
    exit(EXIT_FAILURE);
  }

  // Récupère la valeur par default des différentes variables.
  screen = DefaultScreen(display);
  gc = DefaultGC (display, screen);
  root = RootWindow (display, screen);

  // Gestion des évènements


    XEvent ev;
    char c;



    KeyCode SUPER= XKeysymToKeycode(display, XStringToKeysym("Super_L"));
    KeyCode ALT_L = XKeysymToKeycode(display, XStringToKeysym("Alt_L"));

    KeyCode Z_KEY = XKeysymToKeycode(display, XStringToKeysym("z"));
    KeyCode S_KEY = XKeysymToKeycode(display, XStringToKeysym("s"));
    KeyCode Q_KEY = XKeysymToKeycode(display, XStringToKeysym("q"));
    KeyCode D_KEY = XKeysymToKeycode(display, XStringToKeysym("d"));
    KeyCode O_KEY = XKeysymToKeycode(display, XStringToKeysym("o"));
    KeyCode T_KEY = XKeysymToKeycode(display, XStringToKeysym("t"));
    // TAB

    KeyCode RIGHT = XKeysymToKeycode(display, XStringToKeysym("Right"));
    KeyCode DOWN = XKeysymToKeycode(display, XStringToKeysym("Down"));
    KeyCode LEFT = XKeysymToKeycode(display, XStringToKeysym("Left"));
    KeyCode UP = XKeysymToKeycode(display, XStringToKeysym("Up"));

   
    XGrabKey(display, SUPER, AnyModifier, DefaultRootWindow(display), 1, GrabModeSync, GrabModeSync);
   XGrabKey(display, ALT_L, AnyModifier, DefaultRootWindow(display), 1, GrabModeSync, GrabModeSync);

    for(;;){
        XNextEvent(display, &ev);


        if(ev.type == KeyPress ){ 
    
      if(ev.xkey.keycode == SUPER){
        fprintf(stderr, "got SUPER ALT_L S\n");
        while(ev.type != KeyRelease){
          if(ev.xkey.keycode == Q_KEY)
        fprintf(stderr, "got SUPER ALT_L S\n");
        }
      }

      if (ev.xkey.state & Mod1Mask && ev.xkey.state & Mod4Mask){
        if(ev.xkey.keycode == S_KEY){
        fprintf(stderr, "got SUPER ALT_L S\n");
          if(ev.type == KeyPress)
        fprintf(stderr, "got SUPER ALT_L S\n");
          //printf("%s",exePath);
          //system(strcat(cwd,"twmpowa cmd_relative_move x -70"));
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == Q_KEY){
          if(ev.type == KeyPress)
        fprintf(stderr, "got Alt+g\n");
          
          swallow_keystroke(display, &ev);
        }
        if (ev.xkey.keycode == S_KEY){
          if(ev.type == KeyPress)
        fprintf(stderr, "got Alt+g\n");
          
          swallow_keystroke(display, &ev);
        }
         
        if (ev.xkey.keycode == D_KEY){
          if(ev.type == KeyPress)
        fprintf(stderr, "got Alt+g\n");
          
          swallow_keystroke(display, &ev);
        }
         
        if (ev.xkey.keycode == Z_KEY){
          if(ev.type == KeyPress)
        fprintf(stderr, "got Alt+g\n");
          
          swallow_keystroke(display, &ev);
        }
                  
        if (ev.xkey.keycode == UP){
          if(ev.type == KeyPress)
        fprintf(stderr, "got Alt+g\n");
          
          swallow_keystroke(display, &ev);
        }
         
        if (ev.xkey.keycode == DOWN){
          if(ev.type == KeyPress)
        fprintf(stderr, "got Alt+g\n");
          
          swallow_keystroke(display, &ev);
        }
         
        if (ev.xkey.keycode == LEFT){
          if(ev.type == KeyPress)
        fprintf(stderr, "got Alt+g\n");
          
          swallow_keystroke(display, &ev);
        }
        if (ev.xkey.keycode == RIGHT)
          ;
      }
      else if(ev.xkey.keycode == Q_KEY && ev.xkey.state & Mod4Mask)
        fprintf(stderr, "got Super+g\n");
       
      else if(ev.xkey.state & Mod4Mask){
        fprintf(stderr, "super pressed \n");
        if (ev.xkey.keycode == Q_KEY)
          //                   fprintf(stderr, "got Super+g\n");
          if(ev.type == KeyPress)
        fprintf(stderr, "got Super+g\n");
        
        swallow_keystroke(display, &ev);
        
        
        if (ev.xkey.keycode == S_KEY)
          ;
        if (ev.xkey.keycode == D_KEY)
          ;
        if (ev.xkey.keycode == Z_KEY)
          ;          
        if (ev.xkey.keycode == O_KEY)
          ;
        if (ev.xkey.keycode == T_KEY)
          ; 
      }
      /*
      else if(ev.xkey.keycode == ALT_L){
        if(ev.type == KeyPress)
          fprintf(stderr, "got Alt\n");
        swallow_keystroke(display, &ev);
      }
      */      
      else{
        fprintf(stderr, "got (something else)+F1, passing through\n");
        passthru_keystroke(display, &ev);
      }
    }

    }
    XCloseDisplay(display);
    return EXIT_SUCCESS;
    
    }

    /*
  void buttonPressed(){
    printf("salut");
  }
  */
```

---

### Post by didjoman on 2012-08-11
Ok, I tried something that functions !
My program does differents shortcuts : SUPER + ALT_L + letter or SUPER + letter
Here is the solution I found (if some one else would want to do the same thing ) :

```
#include <X11/Xlib.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <errno.h>

static GC gc; // Contexte graphique                                                                                                                  
static Display* display;
static int screen;
static Window root;


void swallow_keystroke(Display * dpy, XEvent * ev);
void passthru_keystroke(Display * dpy, XEvent * ev);

```

```
#include "events.h"

int main(int argc, char* argv[]){

  char cwd[1024];
  char callFunction[2048];
  getcwd(cwd, sizeof(cwd));

  // Connexion à un serveur X
  display = XOpenDisplay(NULL);
  if(!display){
    printf("Can not open display.\n");
    exit(EXIT_FAILURE);
  }

  // Récupère la valeur par default des différentes variables.
  screen = DefaultScreen(display);
  gc = DefaultGC (display, screen);
  root = RootWindow (display, screen);

  // Gestion des évènements

    XEvent ev;
    char c;

    KeyCode SUPER= XKeysymToKeycode(display, XStringToKeysym("Super_L"));
    KeyCode ALT_L = XKeysymToKeycode(display, XStringToKeysym("Alt_L"));

    KeyCode Z_KEY = XKeysymToKeycode(display, XStringToKeysym("z"));
    KeyCode S_KEY = XKeysymToKeycode(display, XStringToKeysym("s"));
    KeyCode Q_KEY = XKeysymToKeycode(display, XStringToKeysym("q"));
    KeyCode D_KEY = XKeysymToKeycode(display, XStringToKeysym("d"));
    KeyCode F_KEY = XKeysymToKeycode(display, XStringToKeysym("f"));
    KeyCode O_KEY = XKeysymToKeycode(display, XStringToKeysym("o"));
    KeyCode T_KEY = XKeysymToKeycode(display, XStringToKeysym("t"));
    KeyCode M_KEY = XKeysymToKeycode(display, XStringToKeysym("m"));
    // TAB

    KeyCode RIGHT = XKeysymToKeycode(display, XStringToKeysym("Right"));
    KeyCode DOWN = XKeysymToKeycode(display, XStringToKeysym("Down"));
    KeyCode LEFT = XKeysymToKeycode(display, XStringToKeysym("Left"));
    KeyCode UP = XKeysymToKeycode(display, XStringToKeysym("Up"));

    KeyCode KEY_1 = XKeysymToKeycode(display, XStringToKeysym("ampersand"));
    KeyCode KEY_2 = XKeysymToKeycode(display, XStringToKeysym("eacute"));
    KeyCode KEY_3 = XKeysymToKeycode(display, XStringToKeysym("quotedbl"));
    KeyCode KEY_4 = XKeysymToKeycode(display, XStringToKeysym("apostrophe"));
    KeyCode KEY_5 = XKeysymToKeycode(display, XStringToKeysym("parenleft"));
    KeyCode KEY_6 = XKeysymToKeycode(display, XStringToKeysym("minus"));

    /* grab our key combo -- we use AnyModifier because of caps lock/num lock
     * complexity.  just grab every F1 press.
     */
    XGrabKey(display, ALT_L, AnyModifier, DefaultRootWindow(display), 1, GrabModeSync, GrabModeSync);
    XGrabKey(display, SUPER, AnyModifier, DefaultRootWindow(display), 1, GrabModeSync, GrabModeSync);

    int alt_pressed=0;
    int super_pressed=0;

    for(;;){
        XNextEvent(display, &ev);

    if(ev.type == KeyPress){
      // We change the state of boolean variables to know if ALT or SUPER are pressed.
      if(ev.xkey.keycode == ALT_L){
        alt_pressed=1;
        fprintf(stderr, "ALT_L pressed\n");
        swallow_keystroke(display, &ev);
      }
      else if(ev.xkey.keycode == SUPER){
        super_pressed=1;
        fprintf(stderr, "SUPER pressed\n");
        swallow_keystroke(display, &ev);
      }

      // Here are the SUPER + ALT_L + letter keybindings
      else if(alt_pressed == 1 && super_pressed == 1){
        if(ev.xkey.keycode == S_KEY){
          fprintf(stderr, "got SUPER + ALT_L + S\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_resize_all height +40", cwd);
          system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == Q_KEY){
          fprintf(stderr, "got SUPER + ALT_L + Q\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_resize_all width -40", cwd);
          system(callFunction);
          swallow_keystroke(display, &ev);
        }
             
        else if (ev.xkey.keycode == D_KEY){
          fprintf(stderr, "got SUPER + ALT_L + D\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_resize_all width +40", cwd);
          system(callFunction);
          swallow_keystroke(display, &ev);
        }
             
        else if (ev.xkey.keycode == Z_KEY){
          fprintf(stderr, "got SUPER + ALT_L + Z\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_resize_all height -40", cwd);
          system(callFunction);
          swallow_keystroke(display, &ev);
        }
              else if (ev.xkey.keycode == UP){
          fprintf(stderr, "got SUPER +  ALT_L + UP\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_resize height bottom -70", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
             
        else if (ev.xkey.keycode == DOWN){
          fprintf(stderr, "got SUPER +  ALT_L + DOWN\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_resize height bottom +70", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
             
        else if (ev.xkey.keycode == LEFT){
          fprintf(stderr, "got SUPER + ALT_L + LEFT\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_resize width right -70", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == RIGHT){
          fprintf(stderr, "got SUPER + ALT_L + LEFT\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_resize width right +70", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        /*        else{
          fprintf(stderr, "got (something else)+F1, passing through\n");
          passthru_keystroke(display, &ev);
        }
        */

      }
      
    
    
      // Here are the SUPER + letter keybindings
      else if(super_pressed == 1){
        if(ev.xkey.keycode == S_KEY){
          fprintf(stderr, "got SUPER + S\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_half_manage bottom", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == Q_KEY){
          fprintf(stderr, "got SUPER + Q\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_half_manage left", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
             
        else if (ev.xkey.keycode == D_KEY){
          fprintf(stderr, "got SUPER + D\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_half_manage right", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
             
        else if (ev.xkey.keycode == Z_KEY){
          fprintf(stderr, "got SUPER + Z\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_half_manage top", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == F_KEY){
          fprintf(stderr, "got SUPER + F\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_half_manage full", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
              else if (ev.xkey.keycode == UP){
          fprintf(stderr, "got SUPER + UP\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_move y -70", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
             
        else if (ev.xkey.keycode == DOWN){
          fprintf(stderr, "got SUPER + DOWN\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_move y +70", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
             
        else if (ev.xkey.keycode == LEFT){
          fprintf(stderr, "got SUPER + LEFT\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_move x -70", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == RIGHT){
          fprintf(stderr, "got SUPER + LEFT\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_move x +70", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        /*        else if (ev.xkey.keycode == O_KEY){
          fprintf(stderr, "got SUPER + O\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_relative_move x +70", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
          }*/
        else if (ev.xkey.keycode == T_KEY){
          fprintf(stderr, "got SUPER + T\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_killing_feature", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == KEY_1){
          fprintf(stderr, "got SUPER + &\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_organise square", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == KEY_2){
          fprintf(stderr, "got SUPER + é\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_organise specialSquare", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == KEY_3){
          fprintf(stderr, "got SUPER + \"\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_organise horizontal", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == KEY_4){
          fprintf(stderr, "got SUPER + '\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_organise vertical", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == KEY_5){
          fprintf(stderr, "got SUPER + (\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_organise spec1", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == KEY_6){
          fprintf(stderr, "got SUPER + -\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_organise spec2", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == M_KEY){
          fprintf(stderr, "got Alt+g\n");
          sprintf(callFunction,"%s/launch_cmd.sh cmd_minimize", cwd);
              system(callFunction);
          swallow_keystroke(display, &ev);
        }
        else if (ev.xkey.keycode == Q_KEY){
          fprintf(stderr, "got Alt+g\n");
          swallow_keystroke(display, &ev);
        }
        /*
        else{
          fprintf(stderr, "got (something else)+F1, passing through\n");
          passthru_keystroke(display, &ev);
        }
        */
      }
      // If any other key are pressed : 
      /*
      else{
        fprintf(stderr, "got (something else)+F1, passing through\n");
        passthru_keystroke(display, &ev);
      }
      */

    }
    else if(ev.type == KeyRelease){
      if(ev.xkey.keycode == ALT_L){
        alt_pressed=0;
        fprintf(stderr, "ALT_L released\n");
      }
      else if(ev.xkey.keycode == SUPER){
        super_pressed=0;
        fprintf(stderr, "SUPER released\n");
      }
    }
    /*
    else{
      fprintf(stderr, "got (something else)+F1, passing through\n");
      passthru_keystroke(display, &ev);
    }
    */
    }
    XCloseDisplay(display);
    return EXIT_SUCCESS;
    
}


void swallow_keystroke(Display * dpy, XEvent * ev)
{
  XAllowEvents(dpy, AsyncKeyboard, ev->xkey.time);
  /* burp */
}

void passthru_keystroke(Display * dpy, XEvent * ev)
{
  /* pass it through to the app, as if we never intercepted it */
  XAllowEvents(dpy, ReplayKeyboard, ev->xkey.time);
  XFlush(dpy); /* don't forget! */
}
```

---

