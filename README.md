# Chaos Engineering práctico: manos a la obra

Desde hace varios años, la digitalización de las compañías ha provocado que los sistemas de TI hayan pasado de ser un complemento del Negocio a ser “EL” Negocio, produciendo que fallos o pérdidas de servicio en sistemas críticos se conviertan en verdaderas catástrofes para las organizaciones. En esta charla vamos a hablar sobre chaos engineering de forma práctica, analizando la infraestructura y la arquitectura de una aplicación para encontrar los puntos más críticos sobre los que realizar nuestras hipótesis y generar el caos para asegurar la resiliencia de nuestros sistemas.

## Slides utilizadas durante la charla

Podéis descargar las slides utilizadas durante la charla aquí: [http://paradig.ma/Codemotion-CEP](http://paradig.ma/Codemotion-CEP)

## Documentación de Chaos Toolkit

Toda la documentación del framework utilizado durante la charla está disponible aquí: [Chaos Toolkit Docs](https://docs.chaostoolkit.org/)

## Aplicación utilizada

Para la realización de esta charla nos hemos basado en la aplicación bookinfo, incluída en el proyecto de Istio como ejemplo: 

[Bookinfo Application](https://istio.io/latest/docs/examples/bookinfo/)

### Arquitectura de la aplicación

![](https://istio.io/latest/docs/examples/bookinfo/withistio.svg)

## ¿Qué encontrarás en este repositorio?

En el directorio sample-experiments podrás encontrar 3 experimentos de ejemplo:
* terminate-half-ratings-v2-pods.json: Utilizando la extensión de Chaos Toolkit para Kubernetes, nos permitirá terminar los pods del servicio ratings v2 de nuestra aplicación.
* drain-node: Utilizando la extensión de Chaos Toolkit para Kubernetes, nos permitirá drenar uno de los nodos de nuestro cluster por completo.
* reviews-network-latency.json: Utilizando la extensión de Chaos Toolkit para Istio, nos permitirá introducir latencias sobre el servicio reviews v3.

## Instalación de Chaos Toolkit

```
pip install -U chaostoolkit chaostoolkit-kubernetes chaostoolkit-istio
```

Configura el acceso a tu cluster de Kubernetes para que Chaos Toolkit tenga acceso. Si tienes el KUBECONFIG apuntando correctamente, Chaos Toolkit lo utilizará sin necesidad de configurar nada adicional.

## Ejecución de experimentos

```
chaos run sample-experiments/terminate-half-ratings-v2-pods.json
```