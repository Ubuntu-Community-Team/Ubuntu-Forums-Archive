---
title: "[TUTORIAL] Instalar Ares en Ubuntu"
date: 2009-05-19
forum: Software
---

### Post by kubuntero on 2009-05-19
Se que a muchos no les gustaria dejar windows por ares, WLM, juegos etc. Por eso este post es un pequeño aporte a la causa linuxera.

Esto fue probado en Ubuntu Jaunty 9.04, aunque no deberia traer problemas con otras versiones.

Lo primero es aclarar que vamos a hacer creer a Ares que está en windows emulando tal SO. Esto se hace con Wine, uno de los emuladores para programas de windows más famoso, junto con Crossover. Otra cosa q deben tener claro es q el rendimiento gráfico del software no es el mejor. 

[SIZE="6"]1º Instalar Wine[/SIZE]

Para Jaunty 9.04:

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine

```

[SIZE="6"]2º Instalar Ares[/SIZE]

Cuando ya tenemos wine instalado, descargamos la [ultima version de Ares]("http://prdownloads.sourceforge.net/aresgalaxy/aresregular211_installer.exe?download"), hacemos clic derecho sobre el paquete y seleccionamos "Abrir con Wine". (ahora wine abrirá el instalador de Ares tal como si nos encontramos en windows)

Deberia abrirse el instalador de Ares y le damos a siguiente, siguiente, siguiente... y listo, ya lo tienes instalado.

Si al abrirse ares les aparece el aviso de "Instalador de Gecko de Wine", Le dan a "Instalar".


[SIZE="6"]3º Recomendaciones[/SIZE]

[LIST]
[*]Al abrir Ares conectarse manualmente, es decir, ir a "Panel de Control", hacer clic en "Desconectar" y luego en "Conectar". Sino, puede que tu ares quede en "conectando" por siempre xD. Es normal que Ares se demore en conectar (más que en windows)
[/LIST]
[LIST]
[*]Recuerda cambiar la carpeta de descarga a una de tu preferencia
[/LIST]
[LIST]
[*]Para tener a Ares en el menú de Aplicaciones vallan a "Aplicaciones/Wine/Configure Wine". En la Pestaña de aplicaciones, presionar el boton "Añadir Aplicación" y buscan el archivo ares.exe como si estuviean en windows (osea entran a Archivos de programa, ares y seleccionan ares.exe) Luego le dan a aceptar y deberia aparecer la aplicación en el menú dentro del apartado Wine.
[/LIST]
[LIST]
[*]No tratar de maximizar ni minimizar la ventana. Es muy probable que wine se cuelge al tratar de hacerlo.
[/LIST]

**Por lo menos a mi el reproductor de audio de Ares me funciona perfectamente**


Ojalá les sirva este mini howto pa seguir haciendo otros.
Cualquier duda sólo pregunten.

---

