---
title: "Request for help/test - Intel Processors power log bits"
date: 2020-07-21
forum: Ubuntu Development Version
---

### Post by Doug S on 2020-07-21
Hi All,

I am looking for users with modern (Sandy Bridge and newer, 2nd gen and newer) Intel processors willing to do a simple test, and report the results on this thread.

It seems that some processors have some of the logging bits set indicating there has been an overpower event after boot, or even after resume from suspend. Why is this a problem? Well, it actually isn't unless one is attempting to get help from Intel, who will then focus on those bits saying "aghh ha". I am thinking that perhaps the kernel should reset those bits during the boot process.

Requirements: The msr-tools package is required, and the msr module needs to be loaded. Two programs that I wrote are also required.

Example 1, i5-9600K:

```
doug@s18:~$ [COLOR="#FF0000"]sudo su[/COLOR]
root@s18:/home/doug# [COLOR="#FF0000"]modprobe msr[/COLOR]
root@s18:/home/doug# c/[COLOR="#FF0000"]msr-decoder[/COLOR]
How many CPUs?: 6
8.) 0x198: IA32_PERF_STATUS     : CPU 0-5 :   8 :   8 :   8 :   8 :   8 :   8 :
B.) 0x770: IA32_PM_ENABLE: 0 : HWP disable
9.) 0x199: IA32_PERF_CTL        : CPU 0-5 :  10 :   8 :   8 :   8 :   8 :   8 :
C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-5 :   6 :   6 :   6 :   6 :   6 :   6 :
1.) 0x19C: IA32_THERM_STATUS: 88470800 [COLOR="#FF0000"]PWL[/COLOR]
2.) 0x1AA: MSR_MISC_PWR_MGMT: 401CC0 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88450800 [COLOR="#FF0000"]PWL[/COLOR]
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: 4000000 [COLOR="#FF0000"]PL1L[/COLOR]
A.) 0x1FC: MSR_POWER_CTL: 3C005D : C1E disable : EEO disable : RHO disable
root@s18:/home/doug# c/[COLOR="#FF0000"]msr-pwr-log-reset[/COLOR]
root@s18:/home/doug# c/[COLOR="#FF0000"]msr-decoder[/COLOR]
How many CPUs?: 6
8.) 0x198: IA32_PERF_STATUS     : CPU 0-5 :   8 :   8 :   8 :   8 :   8 :   8 :
B.) 0x770: IA32_PM_ENABLE: 0 : HWP disable
9.) 0x199: IA32_PERF_CTL        : CPU 0-5 :  11 :   8 :   8 :  10 :   8 :   8 :
C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-5 :   6 :   6 :   6 :   6 :   6 :   6 :
1.) 0x19C: IA32_THERM_STATUS: 88460000
2.) 0x1AA: MSR_MISC_PWR_MGMT: 401CC0 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88450000
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: 0
A.) 0x1FC: MSR_POWER_CTL: 3C005D : C1E disable : EEO disable : RHO disable
```

Post all of the above output in your reply. The most important output is from the first execution of the msr-decoder program.

Example 2, i7-2600K, which is so old it is missing some of the registers, but also doesn't seem to have the problem:

```
doug@s15:~$ [COLOR="#FF0000"]sudo su[/COLOR]
root@s15:/home/doug# [COLOR="#FF0000"]modprobe msr[/COLOR]
root@s15:/home/doug# c/[COLOR="#FF0000"]msr-decoder[/COLOR]
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  31 :  31 :  31 :  31 :  31 :  31 :  31 :  31 :
rdmsr: CPU 0 cannot read MSR 0x00000770
B.) 0x770: IA32_PM_ENABLE: Command B not found or exited with error status
9.) 0x199: IA32_PERF_CTL        : CPU 0-7 :  31 :  31 :  31 :  31 :  31 :  31 :  31 :  31 :
C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-7 :   6 :   6 :   6 :   6 :   6 :   6 :   6 :   6 :
1.) 0x19C: IA32_THERM_STATUS: 88310000
2.) 0x1AA: MSR_MISC_PWR_MGMT: 400000 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 882C0000
rdmsr: CPU 0 cannot read MSR 0x0000064f
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: Command 4 not found or exited with error status
A.) 0x1FC: MSR_POWER_CTL: 4005D : C1E disable : EEO enable : RHO enable

```
I also have data from a friends i5-6200U (print out number of CPUs is incorrect, since fixed):
```
Output from msr-decoder set for 4 CPUs:
8.) 0x198: IA32_PERF_STATUS     : CPU 0-5 :   5 :   5 :   5 :   5 :   5 :   5 : 
B.) 0x770: IA32_PM_ENABLE: 1 : HWP enable
1.) 0x19C: IA32_THERM_STATUS: 88430800 [COLOR="#FF0000"]PWL[/COLOR] 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 4018C0 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88430800 [COLOR="#FF0000"]PWL[/COLOR] 
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: 14000000 [COLOR="#FF0000"]PL1L MTL[/COLOR] 
A.) 0x1FC: MSR_POWER_CTL: 24005D : C1E disable : EEO enable : RHO enable
5.) 0x771: IA32_HWP_CAPABILITIES (performance): 105171C : high 28 : guaranteed 23 : efficient 5 : lowest 1
6.) 0x774: IA32_HWP_REQUEST:    CPU 0-5 : 
    raw: 80001B04 : 80001B04 : 80001B04 : 80001B04 : 
    min:        4 :        4 :        4 :        4 : 
    max:       27 :       27 :       27 :       27 : 
    des:        0 :        0 :        0 :        0 : 
    epp:      128 :      128 :      128 :      128 : 
    act:        0 :        0 :        0 :        0 : 
7.) 0x777: IA32_HWP_STATUS: 4 : high 4 : guaranteed 0 : efficient 0 : lowest 0

```
msr-decoder program:
```
/*****************************************************************************
*
* run as sudo. Requires msr module to already be loaded, and doesn't check.
* read and decode a few MSR's.
*
* msr-decoder.c 2020.07.17 Smythies
*	use nproc to learn the number of CPUs, instead of the
*	current bush league hard coded number of CPUs.
*	set an arbitrary, but plenty good enough maximum.
*
* msr-decoder.c 2020.07.16 Smythies
*	Reverse yesterdays edit. Total B.S.
*
* msr-decoder.c 2020.07.15 Smythies
*	If the processor is EPP capable, and as of a patch from today,
*	it will be used reagrdless. So reflect in the printing of stuff.
*
* msr-decoder.c 2020.06.23 Smythies
*	RHO and EEO bits of POWER_CTL were backwards.
*
* msr-decoder.c 2020.06.13 Smythies
*	Add EPB, if no-HWP.
*
* msr-decoder.c 2020.06.12 Smythies
*	Only try to display HWP specific registers if HWP is enabled.
*
* msr-decoder.c 2020.06.11 Smythies
*	Examine the bits that Srinivas looks at in his patch.
*	Expand decoding for CPU specific registers, at least the ones I need.
*
* msr-decoder.c 2020.06.09 Smythies
*	I don't seem to have 772, IA32_HWP_REQUEST_PKG.
*	Decoding of IA32_HWP_REQUEST seems incorrect.
*
* msr-decoder.c 2020.06.09 Smythies
*	Want to read and deocde 772, IA32_HWP_REQUEST_PKG.
*
* msr-decoder.c 2020.06.03 Smythies
*	I used sudo prefix, in case I forget to be root (which I often do).
*	The overheads are simply too severe with sudo,
*	causing biased pstate status.
*	eliminate the sudo pre-fix and move the status read to be first.
*	Not renumbering the commands, this needs to be re-written anyhow.
*
* msr-decoder.c 2020.06.02 Smythies
*	Don't exit on some errors, just move on.
*	Then can run it with or without HWP.
*
* msr-decoder.c 2020.06.02 Smythies
*	Srinivas asks for these.
*	Some are also decoded by turbostat.
*	Since these will need to be looked at a lot, automate the decoding.
*	When I want the answer quickly, the code is crap. I want it quick.
*
*****************************************************************************/

#include <stdio.h>
#include <fcntl.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <math.h>

#define MAX_LENGTH 2000          /* maximum line length */
#define MAX_CPUS 64              /* arbitrary */

void main(int argc, char **argv){

   unsigned long long current, temp, per_cpu[MAX_CPUS];
   int i, j, k, hwp_flag, cpus;

   char *cmdcpus = "nproc";
   char *cmd1 = "rdmsr -u 0x19C";
   char *cmd2 = "rdmsr -u 0x1AA";
   char *cmd3 = "rdmsr -u 0x1B1";
   char *cmd4 = "rdmsr -u 0x64F";
   char *cmd5 = "rdmsr -u 0x771";
//   char *cmda = "rdmsr -u 0x772";
   char *cmd6 = "rdmsr -u -a 0x774";
   char *cmd7 = "rdmsr -u 0x777";
   char *cmd8 = "rdmsr --bitfield 15:8 -u -a 0x198";
   char *cmd9 = "rdmsr --bitfield 15:8 -u -a 0x199";
   char *cmda = "rdmsr -u 0x1FC";
   char *cmdb = "rdmsr -u 0x770";
   char *cmdc = "rdmsr --bitfield 3:0 -u -a 0x1B0";
   char buf[MAX_LENGTH];

   FILE *fp;

   printf("How many CPUs?: ");

   if ((fp = popen(cmdcpus, "r")) == NULL) {
      printf("Error opening pipe nproc\n");
      exit(-1);
   }
   fgets(buf, MAX_LENGTH, fp);
   sscanf(buf, "%d", &cpus);
   if(pclose(fp))  {
      printf("nproc command not found or exited with error status\n");
      exit(-1);
   } else {
      printf("%d\n", cpus);
   } /* endif */

   printf("8.) 0x198: IA32_PERF_STATUS     : CPU 0-%d : ", cpus-1);

   if ((fp = popen(cmd8, "r")) == NULL) {
       printf("Error opening pipe 8\n");
       exit(-1);
   }
   for(i = 0; i < cpus; i++){
      fgets(buf, MAX_LENGTH, fp);
      sscanf(buf, "%llu", &current);
      printf("%3llu : ", current);
   } /* endfor */
   if(pclose(fp))  {
      printf("Command 8 not found or exited with error status\n");
      exit(-1);
   } /* endif */
   printf("\n");

   printf("B.) 0x770: IA32_PM_ENABLE: ");

   if ((fp = popen(cmdb, "r")) == NULL) {
       printf("Error opening pipe B\n");
       exit(-1);
   }
   fgets(buf, MAX_LENGTH, fp);
   sscanf(buf, "%llu", &current);
   if(pclose(fp))  {
      printf("Command B not found or exited with error status\n");
      current = 0;
   } else {
      printf("%0llX : HWP ", current);
      if(current & 1){
         printf("enable");
         hwp_flag = 1;
      } else {
         printf("disable");
         hwp_flag = 0;
      } /* endif */
      printf("\n");
   } /* endif */

   if(!hwp_flag){ /* only for not hwp mode */

      printf("9.) 0x199: IA32_PERF_CTL        : CPU 0-%d : ", cpus-1);

      if ((fp = popen(cmd9, "r")) == NULL) {
          printf("Error opening pipe 9\n");
          exit(-1);
      }
      for(i = 0; i < cpus; i++){
         fgets(buf, MAX_LENGTH, fp);
         sscanf(buf, "%llu", &current);
         printf("%3llu : ", current);
      } /* endfor */
      if(pclose(fp))  {
         printf("Command 9 not found or exited with error status\n");
         exit(-1);
      } /* endif */
      printf("\n");

      printf("C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-%d : ", cpus-1);

      if ((fp = popen(cmdc, "r")) == NULL) {
          printf("Error opening pipe 9\n");
          exit(-1);
      }
      for(i = 0; i < cpus; i++){
         fgets(buf, MAX_LENGTH, fp);
         sscanf(buf, "%llu", &current);
         printf("%3llu : ", current);
      } /* endfor */
      if(pclose(fp))  {
         printf("Command 9 not found or exited with error status\n");
         exit(-1);
      } /* endif */
      printf("\n");

   } /* endif */

   printf("1.) 0x19C: IA32_THERM_STATUS: ");

   if ((fp = popen(cmd1, "r")) == NULL) {
       printf("Error opening pipe 1\n");
       exit(-1);
   }
   fgets(buf, MAX_LENGTH, fp);
   sscanf(buf, "%llu", &current);
   if(pclose(fp))  {
      printf("Command 1 not found or exited with error status\n");
   } else {
      printf("%0llX ", current);
      if(current &    1) printf("TS ");
      if(current &    2) printf("TSL ");
      if(current &    4) printf("PHT ");
      if(current &    8) printf("PHTL ");
      if(current &   16) printf("CT ");
      if(current &   32) printf("CTL ");
      if(current &   64) printf("T1 ");
      if(current &  128) printf("T1L ");
      if(current &  256) printf("T2 ");
      if(current &  512) printf("T2L ");
      if(current & 1024) printf("PW ");
      if(current & 2048) printf("PWL ");
      printf("\n");
   } /* endif */

   printf("2.) 0x1AA: MSR_MISC_PWR_MGMT: ");

   if ((fp = popen(cmd2, "r")) == NULL) {
       printf("Error opening pipe 2\n");
       exit(-1);
   }
   fgets(buf, MAX_LENGTH, fp);
   sscanf(buf, "%llu", &current);
   if(pclose(fp))  {
      printf("Command 2 not found or exited with error status\n");
   } else {
      printf("%0llX EIST ", current);
      if(current &    1) printf("disabled "); else printf("enabled ");
      printf("Coordination ");
      if(current & (1 << 22 )) printf("enabled "); else printf("disabled ");
      printf("OOB Bit 8 ");
      if(current & (1 << 8 )) printf("set "); else printf("reset ");
      printf("OOB Bit 18 ");
      if(current & (1 << 18 )) printf("set "); else printf("reset ");
      printf("\n");
   } /* endif */

   printf("3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: ");

   if ((fp = popen(cmd3, "r")) == NULL) {
       printf("Error opening pipe 3\n");
       exit(-1);
   }
   fgets(buf, MAX_LENGTH, fp);
   sscanf(buf, "%llu", &current);
   if(pclose(fp))  {
      printf("Command 3 not found or exited with error status\n");
   } else {
      printf("%0llX ", current);
      if(current &    1) printf("TS ");
      if(current & (1 <<  1)) printf("TSL ");
      if(current & (1 <<  2)) printf("PHT ");
      if(current & (1 <<  3)) printf("PHTL ");
      if(current & (1 <<  4)) printf("CT ");
      if(current & (1 <<  5)) printf("CTL ");
      if(current & (1 <<  6)) printf("T1 ");
      if(current & (1 <<  7)) printf("T1L ");
      if(current & (1 <<  8)) printf("T2 ");
      if(current & (1 <<  9)) printf("T2L ");
      if(current & (1 << 10)) printf("PW ");
      if(current & (1 << 11)) printf("PWL ");
      printf("\n");
   } /* endif */

   printf("4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: ");

   if ((fp = popen(cmd4, "r")) == NULL) {
       printf("Error opening pipe 4\n");
       exit(-1);
   }
   fgets(buf, MAX_LENGTH, fp);
   sscanf(buf, "%llu", &current);
   if(pclose(fp))  {
      printf("Command 4 not found or exited with error status\n");
   } else {
      printf("%0llX ", current);
      if(current &    1) printf("PROCHOT ");
      if(current & (1 <<  1)) printf("T-EVENT ");
      if(current & (1 << 17)) printf("T-EVENTL ");
      if(current & (1 <<  4)) printf("PG-OVERR ");
      if(current & (1 << 20)) printf("PG-OVERRL ");
      if(current & (1 <<  5)) printf("AUTO ");
      if(current & (1 << 21)) printf("AUTOL ");
      if(current & (1 <<  6)) printf("VR ");
      if(current & (1 <<  22)) printf("VRL ");
      if(current & (1 <<  8)) printf("EDP ");
      if(current & (1 << 24)) printf("EDPL ");
      if(current & (1 <<  9)) printf("CP ");
      if(current & (1 << 25)) printf("CPL ");
      if(current & (1 << 10)) printf("PL1 ");
      if(current & (1 << 26)) printf("PL1L ");
      if(current & (1 << 11)) printf("PL2 ");
      if(current & (1 << 27)) printf("PL2L ");
      if(current & (1 << 12)) printf("MT ");
      if(current & (1 << 28)) printf("MTL ");
      if(current & (1 << 13)) printf("TTA ");
      if(current & (1 << 29)) printf("TTAL ");
      printf("\n");
   } /* endif */

   printf("A.) 0x1FC: MSR_POWER_CTL: ");

   if ((fp = popen(cmda, "r")) == NULL) {
       printf("Error opening pipe A\n");
       exit(-1);
   }
   fgets(buf, MAX_LENGTH, fp);
   sscanf(buf, "%llu", &current);
   if(pclose(fp))  {
      printf("Command A not found or exited with error status\n");
   } else {
      printf("%0llX : C1E ", current);
      if(current & (1 <<  1)) printf("enable"); else printf("disable");
      printf(" : EEO ");
      if(current & (1 <<  19)) printf("disable"); else printf("enable");
      printf(" : RHO ");
      if(current & (1 <<  20)) printf("disable"); else printf("enable");
      printf("\n");
   } /* endif */

/* only HWP enabled */
   if(hwp_flag){

      printf("5.) 0x771: IA32_HWP_CAPABILITIES (performance): ");

      if ((fp = popen(cmd5, "r")) == NULL) {
          printf("Error opening pipe 5\n");
          exit(-1);
      }
      fgets(buf, MAX_LENGTH, fp);
      sscanf(buf, "%llu", &current);
      if(pclose(fp))  {
         printf("Command 5 not found or exited with error status\n");
      } else {
         printf("%0llX : high ", current);
         temp = current & 255;
         printf("%llu : guaranteed ", temp);
         temp = (current >> 8) & 255;
         printf("%llu : efficient ", temp);
         temp = (current >> 16) & 255;
         printf("%llu : lowest ", temp);
         temp = (current >> 24) & 255;
         printf("%llu\n", temp);
      } /* endif */

//   printf("a.) 0x772: IA32_HWP_REQUEST_PKG: ");
//
//   if ((fp = popen(cmda, "r")) == NULL) {
//       printf("Error opening pipe 6\n");
//       exit(-1);
//   }
//   fgets(buf, MAX_LENGTH, fp);
//   sscanf(buf, "%llu", &current);
//   if(pclose(fp))  {
//      printf("Command a not found or exited with error status\n");
//   } else {
//      printf("%0llX : min ", current);
//      temp = current & 255;
//      printf("%llu : max ", temp);
//      temp = (current >> 8) & 255;
//      printf("%llu : des ", temp);
//      temp = (current >> 16) & 255;
//      printf("%llu : epp ", temp);
//      temp = (current >> 24) & 255;
//      printf("%llu: act ", temp);
//      temp = (current >> 32) & 1023;
//      printf("%llu\n", temp);
//   } /* endif */

      printf("6.) 0x774: IA32_HWP_REQUEST:    CPU 0-%d : \n", cpus-1);

      if ((fp = popen(cmd6, "r")) == NULL) {
          printf("Error opening pipe 6\n");
          exit(-1);
      }

      for(i = 0; i < cpus; i++){
         fgets(buf, MAX_LENGTH, fp);
         sscanf(buf, "%llu", &per_cpu[i]);
      } /* endfor */

      if(pclose(fp))  {
         printf("Command 6 not found or exited with error status\n");
      } else {
         printf("    raw: ");
         for(i = 0; i < cpus; i++){
            printf("%08llX : ",per_cpu[i]);
         } /* endfor */
         printf("\n    min: ");
         for(i = 0; i < cpus; i++){
            printf("%8llu : ", per_cpu[i] & 255);
         } /* endfor */
         printf("\n    max: ");
         for(i = 0; i < cpus; i++){
            printf("%8llu : ", (per_cpu[i] >> 8) & 255);
         } /* endfor */
          printf("\n    des: ");
          for(i = 0; i < cpus; i++){
             printf("%8llu : ", (per_cpu[i] >> 16) & 255);
          } /* endfor */
          printf("\n    epp: ");
         for(i = 0; i < cpus; i++){
            printf("%8llu : ", (per_cpu[i] >> 24) & 255);
         } /* endfor */
         printf("\n    act: ");
         for(i = 0; i < cpus; i++){
            printf("%8llu : ", (per_cpu[i] >> 32) & 1023);
         } /* endfor */
         printf("\n");
      } /* endif */

      printf("7.) 0x777: IA32_HWP_STATUS: ");

      if ((fp = popen(cmd7, "r")) == NULL) {
          printf("Error opening pipe 7\n");
          exit(-1);
      }
      fgets(buf, MAX_LENGTH, fp);
      sscanf(buf, "%llu", &current);
      if(pclose(fp))  {
         printf("Command 7 not found or exited with error status\n");
      } else {
         printf("%0llX : high ", current);
         temp = current & 255;
         printf("%llu : guaranteed ", temp);
         temp = (current >> 8) & 255;
         printf("%llu : efficient ", temp);
         temp = (current >> 16) & 255;
         printf("%llu : lowest ", temp);
         temp = (current >> 24) & 255;
         printf("%llu\n", temp);
      } /* endif */
   } /* endif */
} /* endprogram */

```
The log bit reset program:
```
/*****************************************************************************
*
* run as sudo. Requires msr module to already be loaded, and doesn't check.
* Some power limit log bits get set during boot or during heavy load.
* i.e. compiling the kernel or prime95 (mrpime) torture test.
* The very excellent power limiting servo in the processor is used
* on purpose for throttling, which in turn keeps the processor temperature
* below 75 degrees.
*
* msr-pwr-log-reset.c 2020.06.12 Smythies
*	Reset the various power log sticky bits.
*
*****************************************************************************/

#include <stdio.h>
#include <fcntl.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <math.h>

#define MAX_LENGTH 2000          /* maximum line length */

int main(int argc, char **argv){

   char buf[MAX_LENGTH];
   FILE *fp;

   sprintf(buf, "wrmsr 0x19c 0");
   if ((fp = popen(buf, "r")) == NULL) {
       printf("Error opening pipe!\n");
       return -1;
   }
   if(pclose(fp))  {
      printf("Command not found or exited with error status\n");
      return -1;
   } /* endif */

   sprintf(buf, "wrmsr 0x1b1 0");
   if ((fp = popen(buf, "r")) == NULL) {
       printf("Error opening pipe!\n");
       return -1;
   }
   if(pclose(fp))  {
      printf("Command not found or exited with error status\n");
      return -1;
   } /* endif */

   sprintf(buf, "wrmsr 0x64f 0");
   if ((fp = popen(buf, "r")) == NULL) {
       printf("Error opening pipe!\n");
       return -1;
   }
   if(pclose(fp))  {
      printf("Command not found or exited with error status\n");
      return -1;
   } /* endif */

   return 0;
} /* endprogram */

```
And if you do not want to compile these yourself, they are also on my website (URL is coded to prevents bots):

double u double u double u dot smythies dot com /~doug/temp_kernel/

My web site has no cookies, no ads, no nothing.

Do the test immediately after boot, before anything else.

**[SIZE=4]EDIT:[/SIZE]** After a PM, adding more information:

If you are not used to compiling c programs, I would suggest you get the pre-compiled versions from my web site and just run them.

i.e.

```
wget double u double u double u dot smythies dot com /~doug/temp_kernel/msr-decoder
wget double u double u double u dot smythies dot com /~doug/temp_kernel/msr-pwr-log-reset
```

You will need to make them executable after wget:

```
chmod 775 msr-decoder
chmod 775 msr-pwr-log-reset
```

Then just run them from the same subdirectory, whereas in my above example I ran them from my c directory.
so:

```
# modrpobe msr
# ./msr-decoder
...
# ./msr-pwr-log-reset
...
# ./msr-decoder
```

Post all of the above output in your reply. The most important output is from the first execution of the msr-decoder program.

You will need the build essentials package of you want to compile yourself. Then:

```
cc msr-decoder.c -o msr-decoder
cc msr-pwr-log-reset.c -o msr-pwr-log-reset
```

---

### Post by Cavsfan on 2020-07-25
With this:
```
root@groovy:/home/cavsfan# inxi -SMC
System:    Host: groovy Kernel: 5.8.0-050800rc6-generic x86_64 bits: 64 Desktop: Xfce 4.14.2 
           Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Desktop System: ASUS product: All Series v: N/A serial: N/A 
           Mobo: ASUSTeK model: Z87-K v: Rev X.0x serial: 130511524103184 UEFI: American Megatrends v: 1103 date: 01/02/2014 
CPU:       Topology: Quad Core model: Intel Core i7-4770K bits: 64 type: MT MCP L2 cache: 8192 KiB 
           Speed: 3720 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 3544 2: 3723 3: 3584 4: 3780 5: 3637 6: 3558 7: 3689 
           8: 3668 



```
This is what I got:
```
root@groovy:/home/cavsfan# ./msr-decoder
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  35 :  35 :  35 :  35 :  35 :  35 :  35 :  35 : 
rdmsr: CPU 0 cannot read MSR 0x00000770
B.) 0x770: IA32_PM_ENABLE: Command B not found or exited with error status
9.) 0x199: IA32_PERF_CTL        : CPU 0-7 :  39 :  39 :  39 :  39 :  39 :  39 :  39 :  39 : 
C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-7 :   6 :   6 :   6 :   6 :   6 :   6 :   6 :   6 : 
1.) 0x19C: IA32_THERM_STATUS: 88430000 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 400000 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88410000 
rdmsr: CPU 0 cannot read MSR 0x0000064f
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: Command 4 not found or exited with error status
A.) 0x1FC: MSR_POWER_CTL: 4005D : C1E disable : EEO enable : RHO enable

```

Is this correct?

---

### Post by Doug S on 2020-07-25
> **Cavsfan said:**
> This is what I got:
```
root@groovy:/home/cavsfan# ./msr-decoder
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  35 :  35 :  35 :  35 :  35 :  35 :  35 :  35 : 
rdmsr: CPU 0 cannot read MSR 0x00000770
B.) 0x770: IA32_PM_ENABLE: Command B not found or exited with error status
9.) 0x199: IA32_PERF_CTL        : CPU 0-7 :  39 :  39 :  39 :  39 :  39 :  39 :  39 :  39 : 
C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-7 :   6 :   6 :   6 :   6 :   6 :   6 :   6 :   6 : 
1.) 0x19C: IA32_THERM_STATUS: 88430000 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 400000 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88410000 
rdmsr: CPU 0 cannot read MSR 0x0000064f
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: Command 4 not found or exited with error status
A.) 0x1FC: MSR_POWER_CTL: 4005D : C1E disable : EEO enable : RHO enable

```

Is this correct?Hi Cavsfan,
Thanks so very much for doing this test. So you had no log bits set directly after re-boot, and did not have to use the bit resetting program at all. O.K. that is very useful information.

Your processor, like my older one, doesn't have some of the MSR's. Nor does it have HWP (HardWare P-state) control. That is all O.K.

---

### Post by Cavsfan on 2020-07-25
> **Cavsfan said:**
> With this:
```
root@groovy:/home/cavsfan# inxi -SMC
System:    Host: groovy Kernel: 5.8.0-050800rc6-generic x86_64 bits: 64 Desktop: Xfce 4.14.2 
           Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Desktop System: ASUS product: All Series v: N/A serial: N/A 
           Mobo: ASUSTeK model: Z87-K v: Rev X.0x serial: 130511524103184 UEFI: American Megatrends v: 1103 date: 01/02/2014 
CPU:       Topology: Quad Core model: Intel Core i7-4770K bits: 64 type: MT MCP L2 cache: 8192 KiB 
           Speed: 3720 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 3544 2: 3723 3: 3584 4: 3780 5: 3637 6: 3558 7: 3689 
           8: 3668 



```
This is what I got:
```
root@groovy:/home/cavsfan# ./msr-decoder
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  35 :  35 :  35 :  35 :  35 :  35 :  35 :  35 : 
rdmsr: CPU 0 cannot read MSR 0x00000770
B.) 0x770: IA32_PM_ENABLE: Command B not found or exited with error status
9.) 0x199: IA32_PERF_CTL        : CPU 0-7 :  39 :  39 :  39 :  39 :  39 :  39 :  39 :  39 : 
C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-7 :   6 :   6 :   6 :   6 :   6 :   6 :   6 :   6 : 
1.) 0x19C: IA32_THERM_STATUS: 88430000 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 400000 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88410000 
rdmsr: CPU 0 cannot read MSR 0x0000064f
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: Command 4 not found or exited with error status
A.) 0x1FC: MSR_POWER_CTL: 4005D : C1E disable : EEO enable : RHO enable

```

Is this correct?

> **Doug S said:**
> Hi Cavsfan,
Thanks so very much for doing this test. So you had no log bits set directly after re-boot, and did not have to use the bit resetting program at all. O.K. that is very useful information.

Your processor, like my older one, doesn't have some of the MSR's. Nor does it have HWP (HardWare P-state) control. That is all O.K.

Glad I could help. It's a 4th generation i7. Still not bad though.

---

### Post by Chanath on 2020-07-25
Should msr-tools be installed, before running ./msr-decorder?

I get this,
```
$ ./msr-decoder
How many CPUs?: 8
sh: 1: rdmsr: not found
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :   8 :   8 :   8 :   8 :   8 :   8 :   8 :   8 : Command 8 not found or exited with error status

```

It is a Lenovo IdeaPad S340-14IIL
```
CPU:
  Topology: Quad Core model: Intel Core i5-1035G1 bits: 64 type: MT MCP 
  L2 cache: 6144 KiB 
  Speed: 1001 MHz min/max: 400/3600 MHz Core speeds (MHz): 1: 992 2: 1000 
  3: 1000 4: 1000 5: 1000 6: 1000 7: 1000 8: 978 

```

---

### Post by Cavsfan on 2020-07-25
> **Chanath said:**
> Should msr-tools be installed, before running ./msr-decorder?

I get this,
```
$ ./msr-decoder
How many CPUs?: 8
sh: 1: rdmsr: not found
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :   8 :   8 :   8 :   8 :   8 :   8 :   8 :   8 : Command 8 not found or exited with error status

```

It is a Lenovo IdeaPad S340-14IIL
```
CPU:
  Topology: Quad Core model: Intel Core i5-1035G1 bits: 64 type: MT MCP 
  L2 cache: 6144 KiB 
  Speed: 1001 MHz min/max: 400/3600 MHz Core speeds (MHz): 1: 992 2: 1000 
  3: 1000 4: 1000 5: 1000 6: 1000 7: 1000 8: 978 

```

Yes

---

### Post by Doug S on 2020-07-25
> **Chanath said:**
> Should msr-tools be installed, before running ./msr-decorder?Yes (and as Cavsfan already replied). It is needed and I don't check if it is loaded. I edited my edit in my original post.

Thank you very much for trying.

---

### Post by Chanath on 2020-07-27
```
# ./msr-decoder
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  12 :  12 :  12 :  12 :  12 :  12 :  12 :  12 : 
B.) 0x770: IA32_PM_ENABLE: 1 : HWP enable
1.) 0x19C: IA32_THERM_STATUS: 88290002 TSL 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 401CC0 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88270002 TSL 
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: 10020000 T-EVENTL MTL 
A.) 0x1FC: MSR_POWER_CTL: 24005F : C1E enable : EEO enable : RHO enable
5.) 0x771: IA32_HWP_CAPABILITIES (performance): 10D0A24 : high 36 : guaranteed 10 : efficient 13 : lowest 1
6.) 0x774: IA32_HWP_REQUEST:    CPU 0-7 : 
    raw: 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 
    min:        4 :        4 :        4 :        4 :        4 :        4 :        4 :        4 : 
    max:       36 :       36 :       36 :       36 :       36 :       36 :       36 :       36 : 
    des:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
    epp:      128 :      128 :      128 :      128 :      128 :      128 :      128 :      128 : 
    act:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
7.) 0x777: IA32_HWP_STATUS: 0 : high 0 : guaranteed 0 : efficient 0 : lowest 0

```
Ideapad s340 14" i5-1035G1

---

### Post by Doug S on 2020-07-27
> **Chanath said:**
> ```
# ./msr-decoder
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  12 :  12 :  12 :  12 :  12 :  12 :  12 :  12 : 
B.) 0x770: IA32_PM_ENABLE: 1 : HWP enable
1.) 0x19C: IA32_THERM_STATUS: 88290002 [COLOR="#FF0000"]TSL[/COLOR] 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 401CC0 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88270002 [COLOR="#FF0000"]TSL[/COLOR] 
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: 10020000 [COLOR="#FF0000"]T-EVENTL MTL[/COLOR] 
A.) 0x1FC: MSR_POWER_CTL: 24005F : C1E enable : EEO enable : RHO enable
5.) 0x771: IA32_HWP_CAPABILITIES (performance): 10D0A24 : high 36 : guaranteed 10 : efficient 13 : lowest 1
6.) 0x774: IA32_HWP_REQUEST:    CPU 0-7 : 
    raw: 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 
    min:        4 :        4 :        4 :        4 :        4 :        4 :        4 :        4 : 
    max:       36 :       36 :       36 :       36 :       36 :       36 :       36 :       36 : 
    des:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
    epp:      128 :      128 :      128 :      128 :      128 :      128 :      128 :      128 : 
    act:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
7.) 0x777: IA32_HWP_STATUS: 0 : high 0 : guaranteed 0 : efficient 0 : lowest 0

```
Ideapad s340 14" i5-1035G1Thank you very much. So you have either had a Thermal event or the bits powered up that way. Interesting. Do they clear and stay cleared if you run the other program, msr-pwr-log-reset? Which I assume you didn't execute yet?

---

### Post by Cavsfan on 2020-07-27
I re-ran the test after a reboot.
```
root@groovy:/home/cavsfan# [COLOR=#ff0000]./msr-decoder[/COLOR]
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  35 :  35 :  35 :  35 :  35 :  35 :  35 :  35 : 
rdmsr: CPU 0 cannot read MSR 0x00000770
B.) 0x770: IA32_PM_ENABLE: Command B not found or exited with error status
9.) 0x199: IA32_PERF_CTL        : CPU 0-7 :  39 :  39 :  39 :  39 :  39 :  39 :  39 :  39 : 
C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-7 :   6 :   6 :   6 :   6 :   6 :   6 :   6 :   6 : 
1.) 0x19C: IA32_THERM_STATUS: 88420000 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 400000 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88410800 [COLOR=#ff0000]PWL[/COLOR] 
rdmsr: CPU 0 cannot read MSR 0x0000064f
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: Command 4 not found or exited with error status
A.) 0x1FC: MSR_POWER_CTL: 4005D : C1E disable : EEO enable : RHO enable
root@groovy:/home/cavsfan# 
root@groovy:/home/cavsfan# [COLOR=#ff0000]./msr-pwr-log-reset[/COLOR]
wrmsr: CPU 0 cannot set MSR 0x0000064f to 0x0000000000000000
Command not found or exited with error status
root@groovy:/home/cavsfan# [COLOR=#ff0000]./msr-decoder[/COLOR]
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  35 :  35 :  35 :  35 :  35 :  35 :  35 :  35 : 
rdmsr: CPU 0 cannot read MSR 0x00000770
B.) 0x770: IA32_PM_ENABLE: Command B not found or exited with error status
9.) 0x199: IA32_PERF_CTL        : CPU 0-7 :  39 :  39 :  39 :  39 :  39 :  39 :  39 :  39 : 
C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-7 :   6 :   6 :   6 :   6 :   6 :   6 :   6 :   6 : 
1.) 0x19C: IA32_THERM_STATUS: 88440000 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 400000 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 88430000 
rdmsr: CPU 0 cannot read MSR 0x0000064f
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: Command 4 not found or exited with error status
A.) 0x1FC: MSR_POWER_CTL: 4005D : C1E disable : EEO enable : RHO enable



```

---

### Post by Chanath on 2020-07-27
This is what I got. Reboted ran both scripts.

```
$ sudo su[sudo] password for akoy: 
root@akoy:/home/akoy# modprobe msr
root@akoy:/home/akoy# ./msr-decoder
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  11 :  11 :  11 :  11 :  11 :  11 :  11 :  11 : 
B.) 0x770: IA32_PM_ENABLE: 1 : HWP enable
1.) 0x19C: IA32_THERM_STATUS: 882B0002 TSL 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 401CC0 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 882A0002 TSL 
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: 10020000 T-EVENTL MTL 
A.) 0x1FC: MSR_POWER_CTL: 24005F : C1E enable : EEO enable : RHO enable
5.) 0x771: IA32_HWP_CAPABILITIES (performance): 10C0A24 : high 36 : guaranteed 10 : efficient 12 : lowest 1
6.) 0x774: IA32_HWP_REQUEST:    CPU 0-7 : 
    raw: 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 
    min:        4 :        4 :        4 :        4 :        4 :        4 :        4 :        4 : 
    max:       36 :       36 :       36 :       36 :       36 :       36 :       36 :       36 : 
    des:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
    epp:      128 :      128 :      128 :      128 :      128 :      128 :      128 :      128 : 
    act:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
7.) 0x777: IA32_HWP_STATUS: 0 : high 0 : guaranteed 0 : efficient 0 : lowest 0
root@akoy:/home/akoy# ./msr-pwr-log-reset
root@akoy:/home/akoy# ./msr-decoder
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  11 :  11 :  11 :  11 :  11 :  11 :  11 :  11 : 
B.) 0x770: IA32_PM_ENABLE: 1 : HWP enable
1.) 0x19C: IA32_THERM_STATUS: 882E0000 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 401CC0 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 882B0000 
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: 10000000 MTL 
A.) 0x1FC: MSR_POWER_CTL: 24005F : C1E enable : EEO enable : RHO enable
5.) 0x771: IA32_HWP_CAPABILITIES (performance): 10C0A24 : high 36 : guaranteed 10 : efficient 12 : lowest 1
6.) 0x774: IA32_HWP_REQUEST:    CPU 0-7 : 
    raw: 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 
    min:        4 :        4 :        4 :        4 :        4 :        4 :        4 :        4 : 
    max:       36 :       36 :       36 :       36 :       36 :       36 :       36 :       36 : 
    des:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
    epp:      128 :      128 :      128 :      128 :      128 :      128 :      128 :      128 : 
    act:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 



```

I have no idea what are you looking for, though. :)

---

### Post by Doug S on 2020-07-27
> **Chanath said:**
> This is what I got. Reboted ran both scripts.

```
$ sudo su[sudo] password for akoy: 
root@akoy:/home/akoy# modprobe msr
root@akoy:/home/akoy# ./msr-decoder
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  11 :  11 :  11 :  11 :  11 :  11 :  11 :  11 : 
B.) 0x770: IA32_PM_ENABLE: 1 : HWP enable
1.) 0x19C: IA32_THERM_STATUS: 882B0002 [COLOR="#FF0000"]TSL[/COLOR] 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 401CC0 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 882A0002 [COLOR="#FF0000"]TSL[/COLOR] 
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: 10020000 [COLOR="#FF0000"]T-EVENTL MTL [/COLOR]
A.) 0x1FC: MSR_POWER_CTL: 24005F : C1E enable : EEO enable : RHO enable
5.) 0x771: IA32_HWP_CAPABILITIES (performance): 10C0A24 : high 36 : guaranteed 10 : efficient 12 : lowest 1
6.) 0x774: IA32_HWP_REQUEST:    CPU 0-7 : 
    raw: 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 
    min:        4 :        4 :        4 :        4 :        4 :        4 :        4 :        4 : 
    max:       36 :       36 :       36 :       36 :       36 :       36 :       36 :       36 : 
    des:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
    epp:      128 :      128 :      128 :      128 :      128 :      128 :      128 :      128 : 
    act:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
7.) 0x777: IA32_HWP_STATUS: 0 : high 0 : guaranteed 0 : efficient 0 : lowest 0
root@akoy:/home/akoy# ./msr-pwr-log-reset
root@akoy:/home/akoy# ./msr-decoder
How many CPUs?: 8
8.) 0x198: IA32_PERF_STATUS     : CPU 0-7 :  11 :  11 :  11 :  11 :  11 :  11 :  11 :  11 : 
B.) 0x770: IA32_PM_ENABLE: 1 : HWP enable
1.) 0x19C: IA32_THERM_STATUS: 882E0000 
2.) 0x1AA: MSR_MISC_PWR_MGMT: 401CC0 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset 
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 882B0000 
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: 10000000 MTL 
A.) 0x1FC: MSR_POWER_CTL: 24005F : C1E enable : EEO enable : RHO enable
5.) 0x771: IA32_HWP_CAPABILITIES (performance): 10C0A24 : high 36 : guaranteed 10 : efficient 12 : lowest 1
6.) 0x774: IA32_HWP_REQUEST:    CPU 0-7 : 
    raw: 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 80002404 : 
    min:        4 :        4 :        4 :        4 :        4 :        4 :        4 :        4 : 
    max:       36 :       36 :       36 :       36 :       36 :       36 :       36 :       36 : 
    des:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 
    epp:      128 :      128 :      128 :      128 :      128 :      128 :      128 :      128 : 
    act:        0 :        0 :        0 :        0 :        0 :        0 :        0 :        0 : 



```

I have no idea what are you looking for, though. :)I am attempting to acquire evidence that several systems startup with some of the logging bits within the processor itself set. These sticky bits would normally indicate that some event, say some power limit has been exceeded for example, has occurred in the past. If the dynamic version of the bit is not also set, then the event has gone away. Your computer is indicating that a thermal event has occurred in the past, but is no longer active.

The background here is that I have been having a spat with Intel for a couple of months now about something with HWP (HardWare P-state) control that doesn't work properly. However we got locked up when my processor was indicating a few power limits had occurred. I simply could not get them to look past those bits and to what was really going on. I also got help from someone with a skylake  i5-6200U, and it had one of the power log bits set after boot, same as Casvan.

In the end I wondering if perhaps those bits should be cleared as part of the Kernel startup stuff, and will propose such if I gather enough proof that it is actually a problem.

---

### Post by Chanath on 2020-07-27
What kind of a thermal event? Is it problematic for the laptop?

---

### Post by Doug S on 2020-07-27
> **Chanath said:**
> What kind of a thermal event? Is it problematic for the laptop?The point with all of this is that I do not know if it was "real" or just the bits started up that way. In my case, and to the best of my abilities, the sticky power log bits were not real. I re-compiled the kernel, forcing the powersave governor during boot and the intel_pstate to be in passive mode. Therefore the CPU should never have gone above 800 MHz, and the processor should have consumed very little power. Yet, those bits were still set. My mains power meter also did not indicate a huge power spike, but its minimum sample interval is only 1 second.  (see attachment)

In your case the bits (multiple registers are saying the same thing) are saying:

> Thermal Log: When set, indicates that the Thermal Status bit has asserted since the log bit was last cleared. This log bit will remain set until cleared by software writing 0.
and

> Maximum Efficiency Frequency Log: When set, indicates that the Maximum Efficiency Frequency Status bit has asserted since the log bit was last cleared. This log bit will remain set until cleared by software writing 0.Although interesting, that bit did not clear.

If your thermal event was indeed real, your LapTop should be fine. That's the whole purpose of the protection. It would have self throttled the CPU frequency to reduce power and therefore thermal load.

Reference: [Intel 64 and IA-32 Architectures Software Developer&#8217;s Manual]("https://software.intel.com/content/www/us/en/develop/articles/intel-sdm.html") (5052 pages)

Note: The mains power would be about 130 Watts when the processor draws engouh power to cause a real over power condition.

---

### Post by Chanath on 2020-07-28
I don't know, if I had a thermal problem. It is a new laptop, manufactured this year. Interestingly, the battery life is better on Linux than on Windows 10. The brightness level can be cranked down to ~35% get a nice paper like look (like reading a newspaper or a book in daylight). But, in Windows, it has to be cranked up to 75% to get that effect. Could be the reason for higher battery life in Windows. I practically never hear the fans, only happens when the laptop is charging, and that's the only time the bottom gets heated. This laptop is on for more than 16 hours everyday, except on Sunday. It gets charged once a day. :)

Btw, I got the same results on Olu-Unity (Ubuntu-Unity), Pop OS and Kubuntu. I suppose it should be, as they are Machine Specific Registers.

---

