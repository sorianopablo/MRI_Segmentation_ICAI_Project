# MRI_Segmentation_ICAI_Project
MRI Segmentation Project for No Structured Data Analysis Subject at ICAI


En este repositorio de GitHub se encuentra documentado el trabajo que hemos realizado Nicolás Núñez de Cela Román, Gonzalo Ruiz Espinar y Pablo Soriano González sobre análisis de datos no estructurados, concretamente sobre imágenes. En este trabajo se han tratado de estudiar datos MRI de niños, imágenes médicas basadas en escáneres tridimensionales del cerebro de niños menores de 6 meses. A estas edades los rangos de intensidad de la materia gris y la materia blanca se sobreponen, dificultando  la segmentación de estas zonas. La correcta segmentación de estas zonas podría ayudar a otros estudios médicos que necesiten diferenciar a qué corresponde cada parte del cerebro.
En el respositorio pueden encontrarse dos NoteBooks diferentes:

## EDA_firstNetwork

En este NoteBook realizamos primero un breve análisis exploratorio de los datos que tenemos. En este proyecto hemos tratado con datos MRI, es decir, imágenes médicas en 3 dimensiones basadas en escáneres. En concreto tenemos dos canales de entrada T1 y T2, correspondientes a dos tipos distintos de escáneres que ofrecen información diferente. Las imágenes que tenemos vienen en formatos que no son legibles de base por lo que es necesario la utilización de librerías para poder convertir las imágenes. En nuestro análisis exploratorio contemplamos distintos cortes en distintos ejes, tanto de los canales de entrada como de las etiquetas de zonas.

Después adaptamos los datos, dividiéndolos en los subconjuntos de Train y Validation y realizando el preprocesado necesario. Tras esto construimos una red. Al tratar de ejecutar nuestra red tenemos problemas pues no conseguimos llevar a cabo el entrenamiento por problemas de memoria, obteniendo siempre el colapso del kérnel, tanto en local como utilizando la versión gratuita de GoogleCollab. En esta línea faltaría ejecutar la red con mayor capacidad de procesamiento para poder obtener resultados y evaluarlos.


## AdaptedNetwork

Debido a la incapacidad de obtener resultados utilizando nuestra red comentada anteriormente decidimos tratar de adaptar una red desarrollada en una tesis de máster con un objetivo similar al nuestro a nuestros datos para poder obtener algunos resultados. De esta manera adaptamos las funciones de esta red en este documento y ejecutamos diferentes pruebas cambiando los parámetros de entrada del modelo y comparando los distintos resultados obtenidos.

Esta red se trata de 3D-Unet (https://arxiv.org/abs/1606.06650).

El número de datos de nuestro dataset es muy limitado (10 sujetos), por lo tanto, en el preprocesado hemos decidido realizar data aumentation, y hemos entrenado subsamples de tamaño (64,64,64) del tamaño original de las imagénes de (144, 192, 256). De este modo aumentamos la muestra de entrenamiento consideramente.

Usando estás técnicas de preprocesmiento, más el estado del arte en arquitecturas de redes neuronales convolucionales para la segmentación, conseguimos obtener segmentar la materia gris, materia blanca, fluido cerebal y fondo de cerebros infantiles con una presición del 82%.

## Analisis_Resultados

En este NoteBook analizamos los resultados obtenidos en los distintos modelos, comentando qué decisiones se han tomado de cara a mejorar el ajuste de los mismos. Representamos en cada uno de los modelos la evolución del DSC y de la Loss Function a lo largo de las diferentes Epochs, tanto para Training como para Validation.

