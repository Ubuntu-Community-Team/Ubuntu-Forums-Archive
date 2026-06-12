---
title: "Recrear mi carpeta de usuario en Karmic"
date: 2009-10-30
forum: Software
---

### Post by EnriqueK on 2009-10-30
Vengo con la misma /home desde la versión 8.04 . hasta ahora todo iba bien para usarla en sucesivas versiones de Ubuntu, pero ahora con KK , algo no anda tan bien, el mayor problema que tengo es que no me aparece en el panel superior el gestor de conexiones que sin embargo si aparece cuando entro en Live CD, cabe aclarar que hasta ahora solo hice pruebas, estas consisten en  primer lugar copiar en un pendrive mi carpeta de usuario , corro el Live CD . creo una cuenta de usuario con mi nombre y contraseá. borro la carpeta de usuario que me genera y enlazo en ese lugar mi verdadera carpeta de usuario que la tengo en el pendrive, este sería en resúmen el proceso que hice siempre antes de decidir instalar una nueva versión y que ahora los resultados no me son del todo satisfactorios.
Estaba pensando en la conveniecia de partir de cero con mi cuenta de usario ya que en todo este tiempo hubieron muchos cambios en por ejemplo kde (uso ambos escritorios), no tendría mayores problemas en recrear todas mis configuraciones, pero quisiera de ser posible poder conservar el menú Aplicaciones ya que tengo allí varios lanzadores personalizados tanto a Scripts que he venido creando, como a aplicaciones que he tenido que crear manualmente por que no las generaba automáticamente. Aclaro que la instalación la haría partiendo de cero pero basada en una lista de paquetes instados en Jaunty.

---

### Post by oktubrer on 2009-11-05
Tendrías que chequear donde están guardadas las modificaciones que le hiciste al menu para hacer un backup de esa carpeta.  ¿Es Lancelot o el default?
Dentro del home, en .kde/share/config están los archivos de configuración de ambos, kickoffrc y lancelotrc
No te aseguro que los lanzadores personalizados se guarden ahí porque no tengo ninguno, pero en teoría debería ser así.

---

