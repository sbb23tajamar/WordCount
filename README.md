
# YARN WORD COUNT

### Paso 1: Clonar y Configurar el Repositorio
Primero, clona el repositorio que contiene un contenedor de Hadoop:

```bash 
git clone big-data-europe/docker-hadoop 
cd docker-hadoop 
docker-compose up -d
```
Este paso puede llevar un tiempo, ya que Docker descargará todas las imágenes y configurará Hadoop. Para verificar que los contenedores se están ejecutando, usa:
```bash 
docker container ps
```

### Paso 2: Acceder al Contenedor namenode

Accede al contenedor de nombre namenode:
```bash 
docker exec -it namenode /bin/bash
```

### Paso 3: Creamos un archivo de prueba

```bash 
vi nombreArchivo.txt
hadoop fs -mkdir /input
hadoop fs -put nombreArchivo.txt /input
```
### Paso 4: Ejecutar el trabajo de Word Count con el siguiente comando de MapReduce

```bash 
hadoop jar $HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-examples-*.jar wordcount /input /output
```
### Paso 5: Revisar el resultado

```bash 
hadoop fs -cat /output/part-r-00000
```

### Paso 6: Apagar los Contenedores
 
```bash 
docker-compose down
```
