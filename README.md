# Detección de Fraude en Transacciones Bancarias mediante el Uso de Autoencoders
La detección eficiente de fraudes en operaciones con tarjetas de crédito ha sido durante mucho tiempo un desafío constante para las instituciones financieras y las empresas. La sofisticación de las técnicas de fraude y el constante desarrollo de nuevas estrategias hacen que la tarea de identificar transacciones fraudulentas sea un aspecto crucial en la seguridad financiera. En este contexto, el empleo de técnicas avanzadas de machine learning, como los autoencoders, ha demostrado ser una solución prometedora para abordar este problema, especialmente en conjuntos de datos altamente desbalanceados.
## Autoencoders
Los autoencoders son una clase de redes neuronales artificiales que se utilizan para el aprendizaje no supervisado de representaciones de datos. La peculiaridad de los autoencoders radica en su capacidad para comprimir datos en un espacio de menor dimensión y, posteriormente, reconstruirlos con alta precisión. Este proceso de compresión y reconstrucción permite la identificación de patrones intrínsecos y la detección de anomalías en los datos.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/autoencoder.png)
### Entrenamiento y Concepto Fundamental
En el caso de la detección de fraudes en transacciones bancarias, el autoencoder se entrena con transacciones **normales**, permitiéndole aprender las características y patrones típicos de estas transacciones. Una vez entrenado, el autoencoder compara las características de una nueva transacción con las que ha aprendido. Si la discrepancia entre la entrada y la salida reconstruida es significativa, el modelo indica que la transacción podría ser **fraudulenta**.

## Exploración del conjunto de datos
El éxito de cualquier técnica de detección de fraudes radica en su capacidad para abordar conjuntos de datos altamente desbalanceados. En este contexto, el conjunto de datos utilizado para este estudio contiene 284315 transacciones normales y tan solo 492 transacciones fraudulentas. La desproporción entre estas clases enfatiza la necesidad de un enfoque que pueda manejar adecuadamente tales desequilibrios. El conjunto de datos con el que se va a trabajar se encuentra disponible en el siguiente [[enlace]][dataset]. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/contador.png)

A priori se podría pensar que la cantidad de dinero que se retira será el factor clave para identificar las transacciones fraudulentas, pero representando los porcentajes de transacciones de cada tipo frente a la cantidad de dinero sacado se puede ver que no es un factor clave en la identificación. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/monto.png)

Realizando un pequeño proceso de exploración de los datos podemos ver que existen características que no presentan diferencia entre los dos típos de transacciones y algunas con una diferencia bastante significativa. Estas diferencias serán la clave que permitirán al modelo distinguir entre ambos tipos. 

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/f1.png)![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/f2.png)

##Diseño y Arquitectura del Modelo
El modelo de autoencoder desarrollado para la detección de fraudes bancarios consta de tres componentes principales:
1. **Encoder:** Esta parte de la red reduce la dimensionalidad de las características de entrada, capturando los patrones más importantes de las transacciones. Consta de una capa de entrada de 29 neuronas, con una capa oculta con 20 neuronas.
2. **Espacio Latente:** Aquí, las características se representan en un espacio de menor dimensión que contiene la información esencial sobre las transacciones. Este presenta 14 dimensiones. 
3. **Decoder: **El Decoder se encarga de reconstruir los datos comprimidos en el espacio latente a su forma original. Presenta una estructura simétrica al Encoder.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/model_autoencoder.png)

La arquitectura simétrica del autoencoder permite la compresión de características y la posterior reconstrucción con el objetivo de minimizar la diferencia entre los datos originales y los reconstruidos.
##Evaluación y Validación del Modelo
Para evaluar la efectividad del modelo de autoencoder en la detección de fraudes, se utiliza el error cuadrático medio (MSE, por sus siglas en inglés) como métrica de rendimiento. Un umbral predefinido se emplea para clasificar las transacciones como normales o fraudulentas. Si el error de reconstrucción excede el umbral, la transacción se identifica como potencialmente fraudulenta.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/CodeCogsEqn.png)

Aunque el modelo presenta ciertos errores al clasificar transacciones normales, la capacidad de identificar con precisión transacciones fraudulentas es un aspecto crucial. La matriz de confusión revela que el modelo logra un rendimiento aceptable al detectar fraudes, incluso si se cometen algunos errores al clasificar transacciones legítimas.

![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/cm.PNG)    ![](https://github.com/JesusFraile/-Credit_Card_Fraud_Detection/blob/main/Images/confusion_matrix.PNG)

## Conclusión
La detección de fraudes en transacciones bancarias a través del uso de autoencoders presenta un enfoque prometedor en la lucha contra el fraude financiero. La capacidad del modelo para aprender patrones de transacciones normales y detectar anomalías en nuevos datos lo convierte en una herramienta valiosa en la prevención de pérdidas financieras y la protección de los activos de los clientes. Si bien los desafíos de los conjuntos de datos desbalanceados persisten, el enfoque de autoencoder demuestra su utilidad y potencial en la detección temprana y precisa de fraudes en el ámbito financiero.


[dataset]: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud 
