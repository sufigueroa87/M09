# 1. Programació multiprocés i paral·lela

- def. multiprocés:
    - Ús de diversos processadors per incrementar el nombre de càlculs per unitat de temps.

## 1.1. Programació multiprocés

- def. multiprocés:
    - Executar diversos processos a la vegada.

### 1.1.1. Procés, sistemes monoprocessador-multiprocessador

- def. procés:
    - activitat realitzada pel processador per tal d'elaborar algun complement, seguint les instruccions d'un programa.

- def. programa:
    - element estàtic, un conjunt d’instruccions, unes línies de codi escrites en un llenguatge de programació, que descriuen el tractament que cal donar a unes dades inicials (d’entrada) per aconseguir el resultat esperat (una sortida concreta).

- def. procés:
    - és dinàmic, és una instància d’un programa en execució, que realitza els canvis indicats pel programa a les dades inicials i obté una sortida concreta. El procés, a més de les instruccions, requerirà també de recursos específics per a l’execució com ara el comptador d’instruccions del programa, el contingut dels registres o les dades.

- qui és l'encarregat de gestionar els processos?
    - el sistema operatiu

- què fa el sistema operatiu quan s'executa un programa?
    - el sistema operatiu crea una instància del programa: el procés.

- què passaria si el programa es tornés a executar?
    - es crearia una nova instància totalment independent a l'anterior (un nou procés) amb les seves pròpies variables, piles i registres.

- on es troba un procés quan està en execució?
    - en memòria

- què té assignats un procés que es troba en execució?
    - els recursos que necessita

- on es guarda la informació associada a l'execució d'un procés?
    - a una estructura de dades

- com es diu la zona on es guarda la informació associada a l'execució d'un procés?
    - BCP: Bloc de Control de Procés

- com es diu el component del maquinari d'un sistema informàtic en el qual s'executen els processos?
    - processador

- def. processador:
    - component de maquinari d’un sistema informàtic encarregat d’executar les instruccions i processar les dades.

- def. sistema monoprocessador:
    - és aquell que està format únicament per un processador

- def. sistema multiprocessador:
    - està format per més d’un processador

- què solen fer la major part dels sistemes operatius quan esperen alguna dada de l'usuari o es troben pendents d'alguna operació d'entrada o sortida?
    - aprofiten el temps de repòs dels processos per introduir al processador un altre procés, simulant així una execució paral·lela

- def. processos concurrents:
    - processos que s'executen a la vegada

- qui és l'encarregat de gestionar l'execució concurrent de diferents processos contra un mateix processador?
    - el sistema operatiu

- def. multiprogramació:
    - quan el sistema operatiu gestiona l'execució de processos concurrents a un sistema monoprocessador

![img.png](img.png)

- què succeeix quan tenim dos o més processadors?
    - es poden executar diversos processos a la vegada

- com s'anomenen també els processadors que tenen més d'un nucli?
    - multiprocessadors

- de quines 3 maneres podem classificar els sistemes multiprocessadors?
    - sistemes multiprocessador fortament acoblats i sistemes multiprocessador dèbilment acoblats

- def. sistemes multiprocessadors fortament acoblats:
    - els diferents processadors comparteixen una mateixa memòria i estan interconnectats a ella a través d’un bus

- en quins 2 grups de sistemes multiprocés es poden classificar els sistemes multiprocessadors fortament acoblats?
    - sistemes multiprocés simètrics / sistemes multiprocés asimètrics

- def. sistemes multiprocés simètrics:
    - els processadors del sistema són de característiques similars i competeixen entre iguals per executar processos

- def. sistemes multiprocés asimètrics:
    - un dels processadors del sistema, el màster, controla la resta de processadors

- com s'anomena també el màster dels sistemes multiprocés asimètrics?
    - master-slave

![img_1.png](img_1.png)

- def. sistemes multiprocessadors dèbilment acoblats:
    - no comparteixen memòria, cada processador té una memòria associada. A les execucions que necessiten col·laboració entre processos els cal l’intercanvi de missatges a través d’enllaços de comunicacions, per habilitar la comunicació entre processos. Un tipus d’aquests sistemes poc acoblats són els sistemes distribuïts, en els quals cada dispositiu monoprocessador (o multiprocessador) podria estar situat a llocs físicament distants.

- exemple de sistema dèbilment acoblat distribuït:
    - una xarxa d’ordinadors o Internet

![img_2.png](img_2.png)

### 1.1.2. Programació concurrent, paral·lela i distribuïda

- def. programació concurrent:
    - quan s’executen en un dispositiu informàtic de forma simultània diferents tasques (processos).

- problemes de l'execució concurrent a l'hora d'accedir a les dades:
    - el bloqueig i la comunicació

- parlem de multiprogramació quan...
    - la programació concurrent es dóna en un computador amb un únic processador

- parlem de programació paral·lela quan...
    - els processos es poden executar de forma realment simultània

- def. programació paral·lela:
    - quan la programació concurrent es realitza en un sistema multiprocessador

![img_3.png](img_3.png)

- principal desavantatge de la programació paral·lela:
    - els controls que hem d'afegir per tal que la comunicació i sincronització dels processos que s'executen concurrentment siguin correctes

![img_4.png](img_4.png)

- programació distribuïda:
    - és un tipus de programació concurrent en la qual els processos són executats en una xarxa de processadors autònoms o en un sistema distribuït. És un sistema de computadors independents que des del punt de vista de l’usuari del sistema es veu com una sola computadora.

- avantatges de la programació distribuïda
    - altament escalables / altament reconfigurables / alta disponibilitat

### 1.1.3. Avantatges i desavantatges del multiprocés

- def. programació concurrent o concurrència:
    - tècnica per la qual múltiples processos s’executen alhora i poden comunicar-se entre ells.

- avantatge : incrementar la potència de càlcul i el rendiment:
    - quan s’executen diversos processos a l’hora, la velocitat d’execució global es pot incrementar.

- avantatge : flexible:
    - si augmenten el processos que s’estan executant és capaç de distribuir la càrrega de treball dels processadors, i pot també reassignar dinàmicament els recursos de memòria i els dispositius per ser més eficients

- avantatge : fàcil creixement:
    - si el sistema ho permet, es poden afegir nous processadors de forma senzilla i així augmenten la seva potència

- avantatge : tolerància a fallades:
    - una fallada d’un processador no fa que el sistema s’aturi.

- avantatge : diferenciar processos per la seva especialització:
    - reservar processadors per operacions complexes, aprofitar-ne d’altres per processaments paral·lels i per avançar l’execució

- inconvenient :
    - vénen provocats sobretot pel control que s’ha de realitzar quan hi ha diversos processos en execució i han de compartir informació o comunicar-se. Això incrementa la complexitat de la programació i penalitza el temps d’execució

## 1.2. Processos i serveis

- def. servei:
    - és un tipus de procés que no té interfície amb l’usuari. Poden ser, depenent de la seva configuració, inicialitzats pel sistema de forma automàtica, en el qual van realitzant les seves funcions sense que l’usuari se n’assabenti o bé es poden mantenir a l’espera que algú els faci una petició per fer una tasca en concret

- classificació dels processos depenent de com s'estan executant:
    - processos en primer pla (foreground, en anglès) i processos en segon pla (background)

- def. processos en primer pla:
    - mantenen una comunicació amb l’usuari, ja sigui informant de les accions realitzades o esperant les seves peticions per mitjà d’alguna interfície d’usuari

- def. processos en segon pla:
    - no es mostren explícitament a l’usuari, bé perquè no els cal la seva intervenció o bé perquè les dades requerides no s’incorporen a través d’una interfície d’usuari

- DAEMON:
    - Disk And Execution Monitor

- de quins tipus de processos estem parlant quan parlem de serveis?
    - processos executats en segon pla

- com es diuen els fitxers de registre on els serveis emmagatzemen la informació generada o les possibles errades que es vagin produïnt?
    - logs

### 1.2.1. Fils i processos

- per què els processos s'anomenen entitats pesades?
    - perquè estan a espais de direccionament de memòria independents, de creació i de comunicació entre processos, cosa que consumeix molts recursos de processador

- per què els fils s'anomenen entitats lleugeres?
    - perquè no consumeixen gaire temps de processador

- quan estarà un procés en execució?
    - mentre algun dels seus fils estiguin actius

- def. fil:
    - els fils comparteixen els recursos del procés (dades, codi, memòria, etc.)

- 2 nivells de fils:
    - fils de nivell d'usuari, que són els que creem quan programem amb un llenguage de programació com ara Java
    - fils de segon nivell, que són els que crea el sistema operatiu per donar suport als primers

## 1.3. Gestió de processos i desenvolupament d’aplicacions amb finalitat de computació paral·lela

### 1.3.1. Estats d'un procés

- def. planificador de processos:
    - encarregat de repartir l’ús del processador de la forma més eficient possible i assegurant que tots els processos s’executin en algun moment

- en què es basa el sistema operatiu per realitzar la planificació de processos?
    - es basarà en l’estat dels processos per saber quins necessitaran l’ús del processador

![img_5.png](img_5.png)

- def. nou:
    - quan un procés és creat

- def. preparat :
    - el procés passa a l'estat preparat

- què segueix el planificador de processos:
    - una política que indica quan un procés ha de canviar d’estat, quan ha de deixar lliure o entrar a fer ús del processador

### 1.3.2. Planificació de processos

- def. planificació de processos:
    - conjunt de protocols o polítiques que decideixen en quin ordre s’executaran els processos al processador. Aquestes polítiques segueixen alguns criteris de prioritat segons la importància del procés, el temps d’utilització del processador, el temps de resposta del procés, etc

- def. planificació a llarg termini:
    - en el moment que es crea un procés es decideixen alguns criteris de planificació, com ara la unitat de temps màxim que un procés podrà romandre en execució (que s’anomena quantum) o la prioritat inicial que se li assignarà a cada procés de forma dinàmica per la utilització del processador

- def. planificació a curt termini:
    - cada vegada que un procés abandona el processador cal prendre la decisió de quin serà el nou procés que entrarà a fer-ne ús. En aquest cas les polítiques intenten minimitzar el temps necessari per aconseguir un canvi de context. Els processos recentment executats solen tenir prioritat però cal assegurar que mai s’exclogui permanentment cap procés de l’execució

- def. planificació a mig termini:
    - existeixen altres parts del sistema operatiu que també són importants a la planificació de processos. En el cas del SWAP de memòria, si es treu un procés de la memòria per problemes d’espai fa que no pugui ser planificable de forma immediata. El planificador a mig termini serà l’encarregat de decidir quan cal portar a la memòria principal les dades dels processos emmagatzemats fora i quines caldrà traslladar de la memòria principal a l’espai d’intercanvi

![img_6.png](img_6.png)

- def. planificació temporal:
    - en el qual es troba definida la política de planificació que actua sobre cada processador de forma individual, com si fos un sistema monoprocessador. El planificador temporal decideix quan de temps cal dedicar a processar cada procés, quan cal fer canviar, per a quin motiu, etc

- def. planificació espacial:
    - en el qual es defineix com es reparteixen els processos entre els processadors. És a dir, organitza quin processador executa quin procés

### 1.3.3. Programació paral·lela transparent

- quines llibreries de baix nivell proporciona Java que dona suport a la programació concurrent?
    - java.lang.Thread
    - java.lang.Runnable

- quins marcs predefinits de programació paral·lela té el llenguatge Java?
    - Executor
    - fork-join

- què fan les llibreries Executor i fork-join?
    - encapsulen bona part de la funcionalitat i amb ella de la complexitat addicional que la programació de més baix nivell (Threads) presenta

#### Us de patrons per resoldre problemes similars

- def. patrons:
    - solucions genèriques que ens permeten resoldre diversos problemes similars canviant petites coses. L’enginyeria informàtica fa servir aquest concepte per referir-se a biblioteques complexes que permeten un alt grau de configuració malgrat que per això sigui necessari escriure aquelles parts específiques que adaptaran el patró al problema que s’intenti resoldre

- què fa la biblioteca Executor de Java?
    - implementa diversos patrons amb l’objectiu de solucionar de la forma més transparent possible bona part de les situacions en les quals es necessita programació paral·lela. Cada patró s’adapta a diferents situacions per la qual cosa cal saber distingir les situacions i aplicar correctament el patró que calgui

![img_7.png](img_7.png)

#### Executor

- com podem simplificar la programació paral·lela?
    - dividir un problema en problemes més petits i cadascun d’aquests subproblemes enviar-los a executar per separat. Per tant, d’una tasca complicada en tenim diverses de més simples. Per poder executar en paral·lel totes aquestes subtasques i així augmentar el rendiment, es creen diferents subprocessos o fils, però aquesta creació és totalment transparent pel programador, és la màquina virtual de Java l’encarregada de gestionar la creació de fils per executar en paral·lel les subtasques

- def. Executor:
    - és una millora sobre la creació de fils, ja que s’abstreu de la creació i la gestió dels subprocessos, De fet només cal indicar la tasca o tasques a realitzar de forma paral·lela (instant objectes de tipus Runnable o Callable), escollir el gestor adequat i deixar que aquest s’encarregui de tot

- de quins 3 tipus de gestors disposem en Java per poder simplificar la programació paral·lela?
    - ThreadPoolExecutor: gestor genèric
    - ScheduledThreadPoolExecutor: gestor capaç de seguir pautes temporals d'execució
    - ForkJoinPool: classe que forma part de java.util.concurrent

##### ThreadPoolExecutor

En Java, la clase equivalente para trabajar con hilos en un entorno similar a un pool de hilos es ExecutorService, y puedes utilizar su implementación específica ThreadPoolExecutor para crear y gestionar un grupo de hilos. Aquí tienes un ejemplo básico:



#### Interface Callable i Future

- què fa la interface Future?
    - conté el valor que es retorna després de l'execució
    - es defineix quan el thread (fil) ha acabat

- què fa la interface Callable?
    - defineix un thread (fil) que retorna un valor

### 1.3.4. Els esdeveniments: concepte, associació d’accions, esdeveniments escoltadors.

### 1.3.5. Edició del codi generat per les eines de disseny

hola

