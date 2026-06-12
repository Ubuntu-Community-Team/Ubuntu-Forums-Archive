---
title: "libraries missing when installing libboost-all-dev with apt-get"
date: 2015-08-18
forum: Repositories &amp; Backports
---

### Post by richard130 on 2015-08-18
Hi,

My code links to the compiled boost libraries (not the headers), but when I ran

```
sudo apt-get install libboost-all-dev
```

I can only find the headers, no library (.a .so) files.

When I run

```
sudo dpkg -L libboost-all-dev
```

I get:

```
/./usr
/usr/share
/usr/share/doc
/usr/share/doc/libboost-all-dev
/usr/share/doc/libboost-all-dev/copyright
/usr/share/doc/libboost-all-dev/changelog.gz



```

I am expecting libraries in /usr/lib/. Where are they?

Rich.

---

### Post by steeldriver on 2015-08-18
libboost-all-dev is just a metapackage: the actual libraries (and headers) get installed via its dependent packages e.g.

```

~$ apt-cache depends libboost-all-dev
libboost-all-dev
  Depends: libboost-dev
  Depends: libboost-tools-dev
    libboost-tools-dev:i386
  Depends: libboost-atomic-dev
  Depends: libboost-chrono-dev
  Depends: libboost-context-dev
  Depends: libboost-coroutine-dev
  Depends: libboost-date-time-dev
  Depends: libboost-exception-dev
  Depends: libboost-filesystem-dev
  Depends: libboost-graph-dev
  Depends: libboost-graph-parallel-dev
  Depends: libboost-iostreams-dev
  Depends: libboost-locale-dev
  Depends: libboost-log-dev
  Depends: libboost-math-dev
  Depends: libboost-mpi-dev
  Depends: libboost-mpi-python-dev
  Depends: libboost-program-options-dev
  Depends: libboost-python-dev
  Depends: libboost-random-dev
  Depends: libboost-regex-dev
  Depends: libboost-serialization-dev
  Depends: libboost-signals-dev
  Depends: libboost-system-dev
  Depends: libboost-test-dev
  Depends: libboost-thread-dev
  Depends: libboost-timer-dev
  Depends: libboost-wave-dev
  Conflicts: libboost-all-dev:i386

```

```

~$ find /usr/lib -name 'libboost*'
/usr/lib/x86_64-linux-gnu/libboost_python-py34.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_unit_test_framework.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_mpi_python-py27.so
/usr/lib/x86_64-linux-gnu/libboost_iostreams.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_python-py34.a
/usr/lib/x86_64-linux-gnu/libboost_mpi_python-py27.a
/usr/lib/x86_64-linux-gnu/libboost_python.a
/usr/lib/x86_64-linux-gnu/libboost_graph.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_regex.a
/usr/lib/x86_64-linux-gnu/libboost_wave.a
/usr/lib/x86_64-linux-gnu/libboost_locale.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_iostreams.so
/usr/lib/x86_64-linux-gnu/libboost_mpi_python-py34.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_python.so
/usr/lib/x86_64-linux-gnu/libboost_date_time.a
/usr/lib/x86_64-linux-gnu/libboost_signals.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_filesystem.a
/usr/lib/x86_64-linux-gnu/libboost_random.a
/usr/lib/x86_64-linux-gnu/libboost_signals.so
/usr/lib/x86_64-linux-gnu/libboost_mpi_python-py27.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_prg_exec_monitor.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_chrono.so
/usr/lib/x86_64-linux-gnu/libboost_math_tr1f.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_math_c99.so
/usr/lib/x86_64-linux-gnu/libboost_atomic.so
/usr/lib/x86_64-linux-gnu/libboost_math_tr1l.a
/usr/lib/x86_64-linux-gnu/libboost_filesystem.so
/usr/lib/x86_64-linux-gnu/libboost_wserialization.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_locale.a
/usr/lib/x86_64-linux-gnu/libboost_regex.so
/usr/lib/x86_64-linux-gnu/libboost_math_c99l.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_system.so
/usr/lib/x86_64-linux-gnu/libboost_date_time.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_thread.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_wserialization.so
/usr/lib/x86_64-linux-gnu/libboost_graph_parallel.so
/usr/lib/x86_64-linux-gnu/libboost_math_tr1.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_locale.so
/usr/lib/x86_64-linux-gnu/libboost_log.so
/usr/lib/x86_64-linux-gnu/libboost_date_time.so
/usr/lib/x86_64-linux-gnu/libboost_chrono.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_log_setup.a
/usr/lib/x86_64-linux-gnu/libboost_test_exec_monitor.a
/usr/lib/x86_64-linux-gnu/libboost_context.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_mpi_python.a
/usr/lib/x86_64-linux-gnu/libboost_log_setup.so
/usr/lib/x86_64-linux-gnu/libboost_program_options.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_unit_test_framework.a
/usr/lib/x86_64-linux-gnu/libboost_python-py34.so
/usr/lib/x86_64-linux-gnu/libboost_random.so
/usr/lib/x86_64-linux-gnu/libboost_math_c99f.a
/usr/lib/x86_64-linux-gnu/libboost_thread.so
/usr/lib/x86_64-linux-gnu/libboost_math_tr1l.so
/usr/lib/x86_64-linux-gnu/libboost_iostreams.a
/usr/lib/x86_64-linux-gnu/libboost_python-py27.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_system.a
/usr/lib/x86_64-linux-gnu/libboost_coroutine.a
/usr/lib/x86_64-linux-gnu/libboost_wave.so
/usr/lib/x86_64-linux-gnu/libboost_context.a
/usr/lib/x86_64-linux-gnu/libboost_mpi_python-py34.so
/usr/lib/x86_64-linux-gnu/libboost_mpi.a
/usr/lib/x86_64-linux-gnu/libboost_graph.a
/usr/lib/x86_64-linux-gnu/libboost_graph_parallel.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_graph_parallel.a
/usr/lib/x86_64-linux-gnu/libboost_atomic.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_math_c99l.so
/usr/lib/x86_64-linux-gnu/libboost_mpi_python-py34.a
/usr/lib/x86_64-linux-gnu/libboost_regex.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_context.so
/usr/lib/x86_64-linux-gnu/libboost_math_tr1f.so
/usr/lib/x86_64-linux-gnu/libboost_system.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_math_tr1.so
/usr/lib/x86_64-linux-gnu/libboost_mpi.so
/usr/lib/x86_64-linux-gnu/libboost_prg_exec_monitor.a
/usr/lib/x86_64-linux-gnu/libboost_math_c99f.so
/usr/lib/x86_64-linux-gnu/libboost_math_c99.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_prg_exec_monitor.so
/usr/lib/x86_64-linux-gnu/libboost_signals.a
/usr/lib/x86_64-linux-gnu/libboost_math_c99.a
/usr/lib/x86_64-linux-gnu/libboost_graph.so
/usr/lib/x86_64-linux-gnu/libboost_math_c99l.a
/usr/lib/x86_64-linux-gnu/libboost_mpi_python.so
/usr/lib/x86_64-linux-gnu/libboost_atomic.a
/usr/lib/x86_64-linux-gnu/libboost_timer.so
/usr/lib/x86_64-linux-gnu/libboost_filesystem.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_wave.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_thread.a
/usr/lib/x86_64-linux-gnu/libboost_timer.a
/usr/lib/x86_64-linux-gnu/libboost_math_tr1l.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_program_options.a
/usr/lib/x86_64-linux-gnu/libboost_math_tr1f.a
/usr/lib/x86_64-linux-gnu/libboost_math_c99f.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_chrono.a
/usr/lib/x86_64-linux-gnu/libboost_python-py27.a
/usr/lib/x86_64-linux-gnu/libboost_serialization.so
/usr/lib/x86_64-linux-gnu/libboost_program_options.so
/usr/lib/x86_64-linux-gnu/libboost_log_setup.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_log.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_log.a
/usr/lib/x86_64-linux-gnu/libboost_unit_test_framework.so
/usr/lib/x86_64-linux-gnu/libboost_serialization.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_math_tr1.a
/usr/lib/x86_64-linux-gnu/libboost_wserialization.a
/usr/lib/x86_64-linux-gnu/libboost_exception.a
/usr/lib/x86_64-linux-gnu/libboost_random.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_serialization.a
/usr/lib/x86_64-linux-gnu/libboost_timer.so.1.54.0
/usr/lib/x86_64-linux-gnu/libboost_python-py27.so
/usr/lib/x86_64-linux-gnu/libboost_mpi.so.1.54.0

```

```

~$ dpkg -S /usr/lib/x86_64-linux-gnu/libboost_mpi.so.1.54.0
libboost-mpi1.54.0: /usr/lib/x86_64-linux-gnu/libboost_mpi.so.1.54.0

```

---

### Post by richard130 on 2015-08-18
Right you are. Found it. Different file structure to what I used last. Thanks,

---

