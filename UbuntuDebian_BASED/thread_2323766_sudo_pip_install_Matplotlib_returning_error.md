---
title: "sudo pip install Matplotlib returning error"
date: 2016-05-08
forum: Ubuntu/Debian BASED
---

### Post by LastDino on 2016-05-08
This isn't really OS related issue but thought it would be best to ask here as this does seem to be some dependency issue.

I'm new to Python (and programming in general) but it was so far so good till I started getting this error
>  sudo pip install MatplotlibThe directory '/home/owl/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/home/owl/.cache/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting Matplotlib
  Downloading matplotlib-1.5.1.tar.gz (54.0MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 54.0MB 17kB/s 
    Complete output from command python setup.py egg_info:
    ============================================================================
    Edit setup.cfg to change the build options
    
    BUILDING MATPLOTLIB
                matplotlib: yes [1.5.1]
                    python: yes [2.7.6 (default, Jun 22 2015, 17:58:13)  [GCC
                            4.8.2]]
                  platform: yes [linux2]
    
    REQUIRED DEPENDENCIES AND EXTENSIONS
                     numpy: yes [version 1.11.0]
                  dateutil: yes [dateutil was not found. It is required for date
                            axis support. pip/easy_install may attempt to
                            install it after matplotlib.]
                      pytz: yes [pytz was not found. pip will attempt to install
                            it after matplotlib.]
                    cycler: yes [cycler was not found. pip will attempt to
                            install it after matplotlib.]
                   tornado: yes [tornado was not found. It is required for the
                            WebAgg backend. pip/easy_install may attempt to
                            install it after matplotlib.]
                 pyparsing: yes [pyparsing was not found. It is required for
                            mathtext support. pip/easy_install may attempt to
                            install it after matplotlib.]
                    libagg: yes [pkg-config information for 'libagg' could not
                            be found. Using local copy.]
                  freetype: no  [The C/C++ header for freetype2 (ft2build.h)
                            could not be found.  You may need to install the
                            development package.]
                       png: yes [version 1.2.50]
                     qhull: yes [pkg-config information for 'qhull' could not be
                            found. Using local copy.]
    
    OPTIONAL SUBPACKAGES
               sample_data: yes [installing]
                  toolkits: yes [installing]
                     tests: yes [nose 0.11.1 or later is required to run the
                            matplotlib test suite. Please install it with pip or
                            your preferred tool to run the test suite / mock is
                            required to run the matplotlib test suite. Please
                            install it with pip or your preferred tool to run
                            the test suite]
            toolkits_tests: yes [nose 0.11.1 or later is required to run the
                            matplotlib test suite. Please install it with pip or
                            your preferred tool to run the test suite / mock is
                            required to run the matplotlib test suite. Please
                            install it with pip or your preferred tool to run
                            the test suite]
    
    OPTIONAL BACKEND EXTENSIONS
                    macosx: no  [Mac OS-X only]
                    qt5agg: no  [PyQt5 not found]
                    qt4agg: yes [installing, Qt: 4.8.6, PyQt: 4.8.6; PySide not
                            found]
                   gtk3agg: yes [installing, version 3.8.10]
                 gtk3cairo: yes [installing, version 3.8.10]
                    gtkagg: no  [The C/C++ header for gtk (gtk/gtk.h) could not
                            be found.  You may need to install the development
                            package.]
                     tkagg: no  [TKAgg requires Tkinter.]
                     wxagg: no  [requires wxPython]
                       gtk: no  [The C/C++ header for gtk (gtk/gtk.h) could not
                            be found.  You may need to install the development
                            package.]
                       agg: yes [installing]
                     cairo: yes [installing, pycairo version 1.8.8]
                 windowing: no  [Microsoft Windows only]
    
    OPTIONAL LATEX DEPENDENCIES
                    dvipng: no
               ghostscript: yes [version 9.10]
                     latex: no
                   pdftops: yes [version 0.24.5]
    
    OPTIONAL PACKAGE DATA
                      dlls: no  [skipping due to configuration]
    
    ============================================================================
                            * The following required packages can not be built:
                            * freetype
    
    ----------------------------------------
**Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-build-e2WHn0/Matplotlib/**




I'm having difficulty determining what the bold part in error means, sorry for bit of ignorance but I've went through threads on Stack overflow and there doesn't seem to be solution to be found and I don't want to just run random commands without actually knowing what it is meant to solve. 

**@Mods**:Also, if this is appropriate for programming section rather than this, I request you to please move the thread. I was in two minds about it so I posted here.
Please help, thanks!

---

