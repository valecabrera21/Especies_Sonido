# **Propuesta de Modelo Original: GeoANF-Net (Geo-Attentive Noisy Fusion Network)**

Proponemos **GeoANF-Net (Geo-Attentive Noisy Fusion Network)** como nuestro modelo original para la clasificación de aves a partir de sus grabaciones bioacústicas.  

La parte innovadora se refleja en combinar información **acústica** correspondiente a los espectrogramas con **datos geoespaciales** correspondientes a la latitud y longitud mediante un mecanismo de **fusión atencional**, lo que permite que las predicciones sean no solo precisas, sino también ecológicamente coherentes con la ubicación donde se registró el sonido.  

A diferencia de los benchmarks (**CNN**, **ResNet** o **EfficientNet**), que trabajan únicamente sobre la representación visual del audio, **GeoANF-Net** considera la información geográfica como una capa adicional de información. 

Esta integración parte del reconocimiento de que las especies presentan **patrones de distribución geográfica específicos**, por lo que una predicción más precisa debe incorporar la **probabilidad ecológica** de que una especie se encuentre en el sitio donde fue registrada la grabación.  

---

## **Arquitectura Propuesta**

La arquitectura de **GeoANF-Net** se compone de tres módulos principales:

1. **Extractor acústico:**  
   Una red convolucional profunda que procesa los espectrogramas y aprende patrones característicos de cada audio.

2. **Procesador geográfico:**  
   Un módulo inspirado en los transformadores que convierte las coordenadas espaciales (latitud y longitud) en vectores representativos del contexto ecológico, permitiendo al modelo “entender” la distribución espacial de las especies.

3. **Fusión atencional cruzada:**  
   Un bloque que combina dinámicamente las características acústicas y geográficas mediante un mecanismo de atención cruzada, ponderando la relevancia de cada modalidad según el registro.  

De esta manera, si un sonido presenta rasgos similares a los de una especie determinada pero proviene de una zona donde esa especie no es común, el modelo puede ajustar su predicción basándose en la información espacial.  



---

## **Diagrama de Flujo del Modelo GeoANF-Net**

```text
Audio → Espectrograma ─┐
                       │          ┌──→ Cross-Attention ─┐
                       ├→ CNN ─────┤                    ├→ Fusión Multimodal Geo-Atenta → Clasificación de Especie
Latitud / Longitud ────┘          └→ Geo-Transformer ───┘
                     ↑
      Iteraciones de pseudoetiquetado (Geo-Noisy Student)

