---
title: "Life Is ..."
date: 2007-03-02
forum: The Cafe
---

### Post by snowboard975 on 2007-03-02
void Life(void)
{
   for (i=0;i<125;i++)
      {
      for (j=0;j<365;j++)
      GetUp();
      DoWhateverCrazyThings();
      Sleep();
      }
      if (GetIllOrAccident()==1) return;
}


Does anybody has better implementation of it??:)

---

### Post by qalimas on 2007-03-02
Well this thread made me unbored for about 10 minutes :D

```
<?php

function dosleep() {
  echo "Sleeping =)<br />";
 }

function dorandstuff() {
  echo "Busy doing random things =D<br />";
 }

$y = 1;
$d = 1;
while ($y < rand(55,76)) {
  $h = 1;
  echo "<br /><br />year $y<br />";
  while ($d < 365) {
    echo "<br /><br />day: $d <br />";
      while ($h < 8) {
        dosleep();
        $h++;
       }
      while ($h == 8 || $h > 8 && $h != 24) {
        dorandstuff();
        $h++;
       }
      if ($h == 24) {
        $d++;
        $h = 1;
       }
    }
  $y++;
  $d = 1;
 }

die("Dead");

?>
```


It works as an actual PHP script :P

---

### Post by shareMenaPeace on 2007-03-02
Not me but reminds me somehow ...


```

/* Source Code Windows 2000 */

#include "win31.h"
#include "win95.h"
#include "win98.h"
#include "workst~1.h"
#include "evenmore.h"
#include "oldstuff.h"
#include "billrulz.h"
#include "monopoly.h"
#include "backdoor.h"
#define INSTALL = HARD

char make_prog_look_big(16000000);
void main()
{
  while(!CRASHED)
  {
    display_copyright_message();
    display_bill_rules_message();
    do_nothing_loop();

    if (first_time_installation)
      {
      make_100_megabyte_swapfile();
      do_nothing_loop();
      totally_screw_up_HPFS_file_system();
      search_and_destroy_the_rest_of-OS2();
      make_futile_attempt_to_damage_Linux();
      disable_Netscape();
      disable_RealPlayer();
      disable_Lotus_Products();
      hang_system();
      } //if
    write_something(anything);
    display_copyright_message();
    do_nothing_loop();
    do_some_stuff();

    if (still_not_crashed)
    {
    display_copyright_message();
    do_nothing_loop();
    basically_run_windows_31();
    do_nothing_loop();
    } // if
  } //while

  if (detect_cache())
    disable_cache();

  if (fast_cpu())
    {
    set_wait_states(lots);
    set_mouse(speed,very_slow);
    set_mouse(action,jumpy);
    set_mouse(reaction,sometimes);
    } //if

  /* printf("Welcome to Windows 3.1");    */
  /* printf("Welcome to Windows 3.11");   */
  /* printf("Welcome to Windows 95");     */
  /* printf("Welcome to Windows NT 3.0"); */
  /* printf("Welcome to Windows 98");     */
  /* printf("Welcome to Windows NT 4.0"); */
  printf("Welcome to Windows 2000");

  if (system_ok())
    crash(to_dos_prompt)
  else
    system_memory = open("a:\swp0001.swp",O_CREATE);

  while(something)
    {
    sleep(5);
    get_user_input();
    sleep(5);
    act_on_user_input();
    sleep(5);
    } // while
  create_general_protection_fault();

} // main

```
[http://www.albinoblacksheep.com/text/source.php](http://www.albinoblacksheep.com/text/source.php)

:P

---

### Post by yabbadabbadont on 2007-03-02
Just a slight modification of your version:

```
void Life(void)
{
        while (! Dead)
        {
                for (j=0;j<365;j++)
                {
                        GetUp();
                        while (AccessGranted) fork();
                        Eat();
                        Sleep();
                }
        }
}

```

---

### Post by beercz on 2007-03-03
... too short to make up code/scripts about life .... :lolflag:

---

