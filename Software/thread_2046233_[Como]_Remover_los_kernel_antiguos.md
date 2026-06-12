---
title: "[Como] Remover los kernel antiguos"
date: 2012-08-22
forum: Software
---

### Post by gmunioz on 2012-08-22
Tanto Siduction como Aptosid tienen un script que permite remover los kernels antiguos del sistema y del menu del Grub, para utilizarlo en principio hace falta instalar: dctrl-tools ssft
En una terminal ejecutamos

sudo su
apt-get install dctrl-tools ssft

Luego es necesario crear el script
ejecutando en una terminal

sudo su
nano /usr/sbin/kernel-remover

Para pegar el el archivo que se abre este contenido

=======comienzo========

#!/bin/sh
#
# we need gettext (is loaded in ssft.sh or cloned...)
if [ -f /usr/bin/gettext.sh ]; then
	. /usr/bin/gettext.sh || exit 1
else
	exit 1
fi
#---------------------------------------------------------------------
# we need root rights
#---------------------------------------------------------------------
if [ "$(id -u)" -ne 0 ]; then
	if [ -x "$(which su-to-root)" ]; then
		[ -n "$DISPLAY" ] &&  exec su-to-root -X -c "${0} $@"
		exec su-to-root -c "${0} $@"
	fi
	printf "ERROR: $0 needs root capabilities, please start it as root.\n\n" >&2
	exit 1
else
	if  test  -n "$DISPLAY"  && ! xset q > /dev/null  2>&1 ; then unset DISPLAY; fi
fi

TEXTDOMAIN="kernel-remover"
export TEXTDOMAIN
TEXTDOMAINDIR=/usr/share/locale
export TEXTDOMAINDIR

#---------------------------------------------------------------------
usage()
{
	echo  "$(basename $0)"
	echo  "     -F parameter    use parameter as the graphical frontend"
	echo  "                     one of text | dialog | kdialog | zenity "
	echo  "     -f              proceed without asking, do complete cleanup"
	echo  "     -h              show this usage"
	exit 1
}
#---------------------------------------------------------------------
force=0
xtra=0
unset frontend
while getopts fhxF: name
do
case $name in
	f)  force=1;;
	F)  frontend="$OPTARG";;
	h)  usage;;
	x)	xtra=1;;
	*)  usage;;
esac
done
shift $(($OPTIND - 1))

#---------------------------------------------------------------------
prepare()
{
	if [ "$force" -eq 0 ]; then
		# we need ssft 
		if [ -f /usr/bin/ssft.sh ]; then
			. /usr/bin/ssft.sh || exit 1
		else
			 echo "Please install the package \"ssft\"."
			 exit 1
		fi
	fi

	if [ -n "${frontend}" ]; then
		case $frontend in
			text)  SSFT_FRONTEND="${frontend}";;
			dialog)  SSFT_FRONTEND="${frontend}";;
			kdialog)  SSFT_FRONTEND="${frontend}";;
			zenity) SSFT_FRONTEND="${frontend}";;
			*)  echo unknown frontend && exit 1;;
		esac
	fi

	if [ -z "$DISPLAY" ] &&  ! /usr/bin/xdpyinfo >/dev/null 2>&1 ; then
		unset DISPLAY
	fi
	if [ -z "$DISPLAY" ]; then
		[ -x /usr/bin/dialog ] && SSFT_FRONTEND=${SSFT_FRONTEND:-"dialog"} || \
			SSFT_FRONTEND=${SSFT_FRONTEND:-"text"}
	else
		if [ -n "$DISPLAY" ] && [ ! -x /usr/bin/zenity ]; then
			if [ -x /usr/bin/dialog ]; then
				SSFT_FRONTEND="dialog"
			else
				SSFT_FRONTEND="text"
			fi
			DISPLAY=""
		else
			SSFT_FRONTEND=${SSFT_FRONTEND:-"zenity"}
		fi
	fi

	# the current one will not be shown in the list ....

	ACTUAL=$(uname -r)
	TITLE="$(gettext "Removing installed kernels")"
	PAD="======="

	[ "${SSFT_FRONTEND}" = "dialog" -o -z "${SSFT_FRONTEND}" ] && \
		CURRENT="$(eval_gettext "The actual (active) kernel is ${PAD}$(uname -r)${PAD}")" || \
		CURRENT="$(eval_gettext "The actual (active) kernel is $(uname -r)")"

}
#---------------------------------------------------------------------
# some useful functions
#---------------------------------------------------------------------
inputbox()
{
	# inputbox Title Text dummy default
	Title="$1"
	Text="$2"
	# $3 not used
	# The default value if used
	SSFT_DEFAULT=$4
	ssft_read_string "${Title}" "${Text}";
}

#---------------------------------------------------------------------
msgbox()
{
	# msgbox title text
	Title="$1"
	Text="$2"
	ssft_display_message "${Title}" "${Text}"
}
#---------------------------------------------------------------------
select_more()
{
	# select one of a list
	Title=$1
	Text=$2
	shift 2
	if ssft_select_multiple "$Title" "$Text" $@ ; then
		Selected=$SSFT_RESULT
		return 0
	else
		return 1 
	fi
}
#---------------------------------------------------------------------
yesno()
{
	# yesno title text width
	Title=$1
	Text=$2
	ssft_yesno "${Title}" "${Text}"
	return $?
}

#---------------------------------------------------------------------
remove_one_kernel()
{
	Kernel=$1 
	if [ "${Kernel}" != "${ACTUAL}" ]; then
		apt-get remove --purge --yes $(dpkg -l | awk "/${Kernel}/{print \$2}")

		dpkg -l "linux-headers-${Kernel}-common" >/dev/null 2>&1 && \
			apt-get remove --purge --yes "linux-headers-${Kernel}-common"
		dpkg -l "linux-support-${Kernel}" >/dev/null 2>&1 && \
			apt-get remove --purge --yes "linux-support-${Kernel}"

		# dispose make install artefacts
		if [ ! -e "/boot/vmlinuz-${Kernel}" ]; then
			rm -rf /lib/modules/${Kernel}
		fi
	else
		# do not remove active kernel
		:
	fi
}

#---------------------------------------------------------------------


get_KernelList()
{
	for v in /boot/vmlinuz-*; do 
		Kernel="$(basename $v | sed s/vmlinuz-//)"
		if [ "${Kernel}" != "${ACTUAL}" ]; then
			meta_package="$(echo $(grep-available \
				-F Depends linux-image-${Kernel} \
				-s Package) | cut -d: -f 2)"

			case $meta_package in
				*$Kernel* ) # this is an old style kernel
					KernelList="${KernelList} ${Kernel}"
					continue
					;;
			esac
			[ -n "${meta_package}" ] && \
				meta_status="$(dpkg-query  -f='${STATUS}\n' \
					-W  ${meta_package}|\
				 	cut -d ' ' -f 3)" || \
				meta_status="not-installed"

			if [ "${meta_status}" = "not-installed" ]; then
				[ -z "${KernelList}" ] && KernelList="${Kernel}" ||\
				KernelList="${KernelList} ${Kernel}"
				# echo KernelList="$KernelList"
			else
				:
			fi
		fi
	done
}

#---------------------------------------------------------------------
# Main
#---------------------------------------------------------------------
if [ "${xtra}" -eq 1 ]; then
	KernelList="$@"
    for i in  ${KernelList} ; do
        removing="$(eval_gettext "removing kernel ${i}")"
        echo $removing
        remove_one_kernel "$i"
    done
    MSG="$(eval_gettext "the following kernels have been removed: \"${KernelList}\"")"
    echo $MSG
    exit 0
fi

prepare

get_KernelList

if [ -z "${KernelList}" ]; then
	MSG="$(gettext "There is only one kernel installed on this system. Nothing to be done!")"
	if [ "${force}" -eq 1 ]; then
		echo "${MSG}"
	else
		msgbox "${TITLE}" "${MSG}"
	fi
	exit 0
fi

if [ "${force}" -eq 1 ]; then
	current="$(eval_gettext "The actual (active) kernel is $(uname -r)")"
	echo ${current}
	for i in  ${KernelList} ; do
		removing="$(eval_gettext "removing kernel ${i}")"
		echo $removing
		remove_one_kernel "$i"
	done
	MSG="$(eval_gettext "the following kernels have been removed: \"${KernelList}\"")"
	echo $MSG
else
	select_more "${TITLE}" "${CURRENT}" ${KernelList} 
	if [ "$?" -ne 0 ]; then
		exit 10
	fi
	if [ -z "${SSFT_RESULT}" ]; then
		exit 12
	fi

	one_removed=false
	for i in ${SSFT_RESULT}; do
		MSG="$i : $(gettext "Should I remove this kernel?") "
		yesno "${TITLE}" "${MSG}"

		if [ "$?" -eq 0 ]; then
			remove_one_kernel "$i"
			one_removed=true
		else
			msgbox "${TiTLE}" "$(gettext "Kernel not removed:") $i"
		fi
	done
fi

exit 0

======final====

Luego es necesario guardar el archivo, cerrar nano y darle permisos de ejecución:

chmod +x /usr/sbin/kernel-remover 

A partir de ahora ejecutando en una terminal

sudo su
kernel-remover

Se podrán remover los kernels antiguos con solo marcarlos y aceptar.

---

### Post by DrKenobi on 2012-09-17
Yo lo hago de otra forma:

Para ver las versiones del Kernel que tenemos:

```
dpkg --get-selections | grep linux-image
```

Luego elimino las que ya no quiero reemplazando las X por lo que corresponda:

```
sudo apt-get remove --purge linux-image-X.X.XX-XX-generic
```

Saludos!

---

### Post by hictio on 2012-09-18
En Lucid Lynx los borraba con Synaptic, más o menos una vez al mes...

[http://oesediez.blogspot.com.ar/2011/03/unwanted-ubuntu-crud-3.html](http://oesediez.blogspot.com.ar/2011/03/unwanted-ubuntu-crud-3.html)

---

### Post by Apipote on 2012-09-23
Ubuntu tweak.
Rápido, facil, seguro.

---

### Post by maximo68 on 2012-10-12
Espectacular Doc, libere bastante espacio

> **DrKenobi said:**
> Yo lo hago de otra forma:

Para ver las versiones del Kernel que tenemos:

```
dpkg --get-selections | grep linux-image
```Luego elimino las que ya no quiero reemplazando las X por lo que corresponda:

```
sudo apt-get remove --purge linux-image-X.X.XX-XX-generic
```Saludos!

---

### Post by guillermolisi on 2012-10-13
> **DrKenobi said:**
> Yo lo hago de otra forma:

Para ver las versiones del Kernel que tenemos:

```
dpkg --get-selections | grep linux-image
```

Luego elimino las que ya no quiero reemplazando las X por lo que corresponda:

```
sudo apt-get remove --purge linux-image-X.X.XX-XX-generic
```

Saludos!
La diferencia respecto de los otros metodos es que de esta forma no se eliminan las instancias de los headers correspondientes a las imagenes que se quieran borrar.

---

### Post by z37a on 2012-10-17
Aparte de todo esto que estan escribiendo quiero aportar un granito de arena mas, SIEMPRE intenten dejar un kernel anterior, no vaya a ser que actualizan y al borrar todos menos el ultimo este falle (cosa que puede fallar) y despues se queden sin sistema!!!!!

---

### Post by guillermolisi on 2012-10-17
> **z37a said:**
> Aparte de todo esto que estan escribiendo quiero aportar un granito de arena mas, SIEMPRE intenten dejar un kernel anterior, no vaya a ser que actualizan y al borrar todos menos el ultimo este falle (cosa que puede fallar) y despues se queden sin sistema!!!!!

Correcto. Es una de las mejores practicas que siempre recomiendo tambien y mas de una vez me ha salvado mas que el dia.

---

### Post by hictio on 2012-10-18
Y para saber la versión del kernel está en uso actualmente (el que NO hay que desinstalar bajo ningún concepto), tipear en un terminal:

```

uname -a ENTER

```

Devuelve algo similar a:
```

Linux stilgar 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:32:50 UTC 2012 i686 i686 i386 GNU/Linux

```

Donde **3.2.0-32-generic** corresponde a la versión del kernel.
Ese kernel NO se puede desisntalar, y como bien sugirieron arriba, hay que mantener como mínimo la versión anterior, por si las moscas.

---

