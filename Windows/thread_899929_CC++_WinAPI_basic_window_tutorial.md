---
title: "C/C++ WinAPI basic window tutorial"
date: 2008-08-24
forum: Windows
---

### Post by jrockpunk1 on 2008-08-24
**tutorial on C or C++ basic window creation**

OK first, Ill start off by writing the code:


```

#include <windows.h>

const char g_szClassName[] = "WindowClass";

LRESULT CALLBACK WinProc(HWND hwnd, UINT msg, WPARAM wParam, LPARAM lParam) //1:identifies window 2:message 3&4:extras for msg
{
        switch(msg)
        {
             case WM_CLOSE:
                  DestroyWindow(hwnd);
                  break;    
             case WM_DESTROY:
                  PostQuitMessage(0);
                  break;
             default:  
                  return DefWindowProc(hwnd, msg, wParam, lParam);
        }
        return 0;
}

int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int iCmdShow)
{
    
    WNDCLASSEX wc;
    HWND hwnd;
    MSG msg;
    
    wc.cbSize        = sizeof(WNDCLASSEX);
    wc.style         = 0;
    wc.lpfnWndProc   = WinProc;
    wc.cbClsExtra    = 0;
    wc.cbWndExtra    = 0;
    wc.hInstance     = hInstance;
    wc.hIcon         = LoadIcon(NULL, IDI_APPLICATION);
    wc.hCursor       = LoadCursor(NULL, IDC_ARROW);
    wc.hbrBackground = (HBRUSH)(COLOR_WINDOW+1);
    wc.lpszMenuName  = NULL;
    wc.lpszClassName = g_szClassName;
    wc.hIconSm       = LoadIcon(NULL, IDI_APPLICATION);
    
    if(!RegisterClassEx(&wc))
    {
         MessageBox(NULL,"error registering window!", "FAIL!", MB_ICONEXCLAMATION | MB_OK);
         return 0;
    }
    
        hwnd = CreateWindowEx(
        WS_EX_CLIENTEDGE,
        g_szClassName,
        "The title of my window",
        WS_OVERLAPPEDWINDOW,
        CW_USEDEFAULT, CW_USEDEFAULT, 240, 120,
        NULL, NULL, hInstance, NULL);

    
    if(hwnd==NULL)
    {
         MessageBox(NULL, "error creating window!", ":o", MB_ICONEXCLAMATION | MB_OK);
         return 0;
    }
    
    ShowWindow(hwnd, iCmdShow);
    UpdateWindow(hwnd);
    
    while(GetMessage(&msg, NULL, 0, 0)>0)
    {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
    }
    
    return msg.wParam;
}

```


ok now lets go over it.

first things first, the functions:

```

int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int iCmdShow)

```


this is the winAPI equivalent to the C/C++ "int main". all the code you want executed goes in here from a beginners point of view, although well soon see this is not exactly the case.
The first paramater is a handle to the programs .exe in memory. the second always returns NULL and is not needed but for some reason has never been changed so you dont have to put it in. the third is the command line arguments in one string, that DOESNT include the program name. The last one has an integer value and has to be used in the ShowWindow() function later.


```

LRESULT CALLBACK WinProc(HWND hwnd, UINT msg, WPARAM wParam, LPARAM lParam)

```


this is the function that processes the code and tells the computer what it wants done. this part of the program is what will keep everything going.
the first paramater identifies the current window it is using in the function. the second is the message you want the function to respond to. the third and fourth are "addons" or "extras" that go into more detail on the second paramater.

now on to this line:

```

const char g_szClassName[] = "WindowClass";

```

that names the window class which you will need if opening multiple windows.

now on to these lines:


```

WNDCLASSEX wc;
HWND hwnd;
MSG msg;

```


the first, WNDCLASSEX is a struct of the window you shall be using. it has just declared an object of the struct called wc. you can generally call this anything you want. (for all you C++ programmers, this struct acts just like a class).
the next creates the name of the window.
the next creates the message that needs to be passed to WinProc.


```

wc.cbSize        = sizeof(WNDCLASSEX);
    wc.style         = 0;
    wc.lpfnWndProc   = WinProc;
    wc.cbClsExtra    = 0;
    wc.cbWndExtra    = 0;
    wc.hInstance     = hInstance;
    wc.hIcon         = LoadIcon(NULL, IDI_APPLICATION);
    wc.hCursor       = LoadCursor(NULL, IDC_ARROW);
    wc.hbrBackground = (HBRUSH)(COLOR_WINDOW+1);
    wc.lpszMenuName  = NULL;
    wc.lpszClassName = g_szClassName;
    wc.hIconSm       = LoadIcon(NULL, IDI_APPLICATION);

```


this code you generally dont have to remember. most programmers dont learn each member of the registration classes, they simply copy and paste them, and edit them to their will. These basically "register" your window (say what it should be like, but doesnt create it). you can look up the members of WNDCLASSEX on the web or in your help files.


```

if(!RegisterClassEx(&wc))
    {
         MessageBox(NULL,"error registering window!", "FAIL!", MB_ICONEXCLAMATION | MB_OK);
         return 0;
    }

```


this code pretty much is self explanitory. RegisterClassEx is a function that returns a boolean value of true if the window has registered. you pass the memory address (pass by reference) of your window class object you created. MessageBox() is a function that displays a messagebox. the first paramater i dont know what does, but i was told to set it to NULL. the next is what you want displayed in the box. the next is the title, and the next i have put as MB_ICONEXCLAMATION | MB_OK. you can have this just as MB_OK, so that it has an OK button that you can click off.
this basically displays an error if it couldnt register the window.


```

hwnd = CreateWindowEx(
        WS_EX_CLIENTEDGE,
        g_szClassName,
        "The title of my window",
        WS_OVERLAPPEDWINDOW,
        CW_USEDEFAULT, CW_USEDEFAULT, 240, 120,
        NULL, NULL, hInstance, NULL);

```


again, this is the same as registering the window, you can just copy and paste it, and edit it to your will. this creates your window.


```

if(hwnd==NULL)
    {
         MessageBox(NULL, "error creating window!", ":o", MB_ICONEXCLAMATION | MB_OK);
         return 0;
    }

```


this is the same as the last one. the only major difference is the line if(hwnd == NULL), where hwnd is the window, and if its null (hasnt been made), display an error.


```

ShowWindow(hwnd, iCmdShow);
UpdateWindow(hwnd);

```


again, speaking for itself, this shows the window and checks and updates it. the first paramater of ShowWindow() is just the current window, and the second gives the user the choice to start with it visible, maximised or minimised, but you could simply pass in SW_SHOWNORMAL all the time and be done with it.


```

while(GetMessage(&msg, NULL, 0, 0)>0)
    {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
    }

```


now this is one of the main parts of WinMain. this basically says, while there are more messages than 0, translate the message, and dispatch it. so say if there was a paint program, there would be a msg something like WM_PAINT. and as soon as there became more than one message (every time you painted), it would update the window and thus give the "painting" effect. quite frankly i dont know the ins and outs of it, but the first paramater is the memory address of the messgae, and i dont know what the 2nd 3rd and 4th are for tongue.gif

Now on to the other function:


```

LRESULT CALLBACK WinProc(HWND hwnd, UINT msg, WPARAM wParam, LPARAM lParam) //1:identifies window 2:message 3&4:extras for msg
{
        switch(msg)
        {
             case WM_CLOSE:
                  DestroyWindow(hwnd);
                  break;    
             case WM_DESTROY:
                  PostQuitMessage(0);
                  break;
             default:  
                  return DefWindowProc(hwnd, msg, wParam, lParam);
        }
        return 0;
}

```


now ive already gone through the paramaters, so on to the function itself. it basically tells the computer what to do in different circumstances. for instance, take the line:

```

case WM_CLOSE:
     DestroyWindow(hwnd);
     break;

```

this says if the program is closed, destroy the window, and exit the switch statement, and thus return 0.
the second says if the window is destroyed quit the program (PostQuitMessage(0)wink.gif
the third is the default. that means f none of the above is met, just make it a normal window that can be maximised, minimised, resized and closed.

you can add much more to this. for instance, take a look at this program:


```

#include <windows.h>

const char g_szClassName[] = "myWindowClass";

LRESULT CALLBACK WndProc(HWND hwnd, UINT msg, WPARAM wParam, LPARAM lParam)
{
    switch(msg)
    {
        case WM_LBUTTONDOWN:
        {
            char szFileName[MAX_PATH];
            HINSTANCE hInstance = GetModuleHandle(NULL);

            GetModuleFileName(hInstance, szFileName, MAX_PATH);
            MessageBox(hwnd, szFileName, "This program is:", MB_OK | MB_ICONINFORMATION);
        }
        break;
        case WM_CLOSE:
            DestroyWindow(hwnd);
        break;
        case WM_DESTROY:
            PostQuitMessage(0);
        break;
        default:
            return DefWindowProc(hwnd, msg, wParam, lParam);
    }
    return 0;
}

int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance,
    LPSTR lpCmdLine, int nCmdShow)
{
    WNDCLASSEX wc;
    HWND hwnd;
    MSG Msg;

    wc.cbSize        = sizeof(WNDCLASSEX);
    wc.style         = 0;
    wc.lpfnWndProc   = WndProc;
    wc.cbClsExtra    = 0;
    wc.cbWndExtra    = 0;
    wc.hInstance     = hInstance;
    wc.hIcon         = LoadIcon(NULL, IDI_APPLICATION);
    wc.hCursor       = LoadCursor(NULL, IDC_ARROW);
    wc.hbrBackground = (HBRUSH)(COLOR_WINDOW+1);
    wc.lpszMenuName  = NULL;
    wc.lpszClassName = g_szClassName;
    wc.hIconSm       = LoadIcon(NULL, IDI_APPLICATION);

    if(!RegisterClassEx(&wc))
    {
        MessageBox(NULL, "Window Registration Failed!", "Error!",
            MB_ICONEXCLAMATION | MB_OK);
        return 0;
    }

    hwnd = CreateWindowEx(
        WS_EX_CLIENTEDGE,
        g_szClassName,
        "The title of my window",
        WS_OVERLAPPEDWINDOW,
        CW_USEDEFAULT, CW_USEDEFAULT, 240, 120,
        NULL, NULL, hInstance, NULL);

    if(hwnd == NULL)
    {
        MessageBox(NULL, "Window Creation Failed!", "Error!",
            MB_ICONEXCLAMATION | MB_OK);
        return 0;
    }

    ShowWindow(hwnd, nCmdShow);
    UpdateWindow(hwnd);

    while(GetMessage(&Msg, NULL, 0, 0) > 0)
    {
        TranslateMessage(&Msg);
        DispatchMessage(&Msg);
    }
    return Msg.wParam;
}

```



i admittedly copied and pasted that. im not going to TOO much trouble to explain to you. as you can see when youve tested it, its created another condition, that if you click on it, it displays where the prgram is located.

thanks for reading, i hope it has helped and you shall want to continue into the realms of API programming biggrin.gif

---

### Post by jpeddicord on 2008-08-25
Umm... this is a Linux forum, so I don't really think this counts as a tutorial (especially if it was copied from an external site).

Moved to Windows Discussions.

---

### Post by fiddledd on 2008-08-25
I bet the OP has posted in the wrong sub-forum. The post is started as if people were expecting it. I certainly wasn't.:)

---

