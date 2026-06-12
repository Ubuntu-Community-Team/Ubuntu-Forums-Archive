---
title: "ayuda para compilar aircrack-ng en la fonera"
date: 2009-08-18
forum: Software
---

### Post by berni69 on 2009-08-18
Buenas tardes a todos, esta vez necesitaria algo de ayuda al compilar el aircrack en un enotrno cruzado, he compilado las teoricas dependencias del programa (openssl) para mi arquitectura, he configurado los maquefiles, common.mak,... y las variables del entorno de compilacion del toolchain del openwrt.


```
bernat@bernat-laptop:~/Escriptori/aircrack-ng-1.0-rc4$ make
make -C src all
make[1]: Entering directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src'
make -C osdep
make[2]: Entering directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src/osdep'
Building for Linux
make[3]: Entering directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src/osdep'
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o osdep.o osdep.c
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o network.o network.c
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o linux.o linux.c
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o linux_tap.o linux_tap.c
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o radiotap/radiotap-parser.o radiotap/radiotap-parser.c
radiotap/radiotap-parser.c: In function 'ieee80211_radiotap_iterator_init':
radiotap/radiotap-parser.c:57: error: 'u_int16_t' undeclared (first use in this function)
radiotap/radiotap-parser.c:57: error: (Each undeclared identifier is reported only once
radiotap/radiotap-parser.c:57: error: for each function it appears in.)
radiotap/radiotap-parser.c:57: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:57: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:61: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:61: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:63: error: 'u_int32_t' undeclared (first use in this function)
radiotap/radiotap-parser.c:63: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:63: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:63: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:63: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:72: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:72: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:72: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:72: error: expected ')' before numeric constant
radiotap/radiotap-parser.c: In function 'ieee80211_radiotap_iterator_next':
radiotap/radiotap-parser.c:225: error: 'u_int32_t' undeclared (first use in this function)
radiotap/radiotap-parser.c:225: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:225: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:225: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:225: error: expected ')' before numeric constant
make[3]: *** [radiotap/radiotap-parser.o] Error 1
make[3]: Leaving directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src/osdep'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src/osdep'
make[1]: *** [osd] Error 2
make[1]: Leaving directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src'
make: *** [all] Error 2
```

este mismo error lo obtengo si en el nombre del sistema en lugar de poner linux pongo linux-mips, mips,... pero lo obtengo ya al compilar el ejecutable airdecloak-ng, los ejecutables que he creado se ejecutan, muestran la ayuda, pero a la hora de escanear o alguna otra cosilla no hacen nada... 

Alguien tiene alguna solucion?

---

