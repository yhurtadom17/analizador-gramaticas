# Analizador de Gramáticas

Un analizador interactivo de gramáticas formales que soporta dos tipos de parsers: **LL(1)** y **SLR(1)**. Esta herramienta te permite construir gramáticas, visualizar conjuntos First/Follow, generar tablas de análisis y validar cadenas de entrada.

## 🎯 Características

- **Parser LL(1)**: Análisis sintáctico descendente con tabla de análisis predictiva
- **Parser SLR(1)**: Análisis sintáctico ascendente con autómata LR(0)
- **Cálculo automático de First y Follow**: Visualización clara de todos los conjuntos
- **Generación de tablas de análisis**: Tablas LL(1) y SLR(1) interactivas
- **Análisis paso a paso**: Traza completa de la ejecución del parser
- **Detección de conflictos**: Identifica si la gramática es válida para el parser seleccionado
- **Interfaz intuitiva**: Diseño limpio con Tailwind CSS

## 🚀 Inicio Rápido

### Requisitos
- Navegador web moderno (Chrome, Firefox, Safari, Edge)
- Sin instalación requerida

### Uso

1. **Abre el archivo** `index.html` en tu navegador
2. **Define tu gramática** en el formato especificado
3. **Selecciona el tipo de parser** (LL(1) o SLR(1))
4. **Ingresa una cadena de entrada** (opcional)
5. **Haz clic en "Analizar Gramática"**

## 📝 Formato de Gramática

### Sintaxis Básica

```
S -> a S | b
A -> a A | ε
B -> x | y z | ε
```

### Reglas

- Usa `->` para separar lado izquierdo (no terminal) del lado derecho
- Usa `|` para separar alternativas (producciones)
- Usa `ε` o `eps` para representar producciones vacías
- Puedes separar tokens por espacios para símbolos multi-carácter
- Las líneas que comienzan con `#` son comentarios
- Las líneas vacías se ignoran

### Ejemplos

**Ejemplo 1:**
```
E -> T E'
E' -> + T E' | ε
T -> F T'
T' -> * F T' | ε
F -> ( E ) | id
```

## 📊 Interpretación de Resultados

### Conjuntos First (Primero)

Muestra los terminales que pueden aparecer al inicio de una derivación

### Conjuntos Follow (Siguiente)

Muestra los terminales que pueden seguir a un no terminal en alguna derivación

### Tablas de Análisis

**LL(1)**: Tabla de decisión para parsers descendentes predictivos
**SLR(1)**: Tabla de acciones (shift/reduce) y gotos para parsers ascendentes

### Análisis Paso a Paso

Traza completa del proceso de parsing mostrando:
- **Pila**: Contenido actual de la pila de análisis
- **Entrada**: Símbolos restantes por procesar
- **Acción**: Operación realizada (match, shift, reduce, aceptar)

## ⚙️ Componentes Técnicos

### Parser LL(1)
- Análisis descendente predictivo
- Basado en tabla M[A, a]
- Utiliza conjuntos First y Follow
- Válido para gramáticas LL(1)

### Parser SLR(1)
- Análisis ascendente con lookahead
- Construcción de autómata LR(0)
- Tablas de acción y goto
- Más potente que LL(1), soporta más gramáticas

### Algoritmos Implementados
- Cálculo de conjuntos First (punto fijo)
- Cálculo de conjuntos Follow (punto fijo)
- Cierre de items (closure)
- Función goto para estados LR(0)
- Tablas de análisis LL(1) y SLR(1)

## 🛠️ Stack Tecnológico

- **React 18**: Biblioteca UI
- **Babel**: Transpilación JSX en tiempo real
- **Tailwind CSS**: Estilos responsive
- **JavaScript Vanilla**: Lógica de parsing

## 📚 Teoría de Compiladores

Este proyecto implementa conceptos fundamentales de teoría de compiladores:

- **Análisis Léxico**: Tokenización de entrada
- **Análisis Sintáctico**: Parsing descendente (LL) y ascendente (SLR)
- **Autómatas**: Construcción de autómatas finitos para LR(0)
- **Gramáticas Formales**: Derivaciones y arboles de análisis

## 🐛 Limitaciones Conocidas

- Máximo 2000 pasos de análisis (previene bucles infinitos)
- Símbolos no terminales deben ser caracteres únicos o palabras separadas por espacios
- No soporta producciones con símbolos especiales complejos
- La detección de conflictos LL(1)/SLR(1) es básica

## 💡 Ejemplos de Uso

### Ejemplo: Para un LL1

```
E -> T E'
E' -> + T E' | ε
T -> F T'
T' -> * F T' | ε
F -> ( E ) | id
```

**Entrada válida**: `id + id * id`

### Ejemplo: Para el SLR(1)

```
E -> E + T | T
T -> T * F | F | ( E )
F -> id
```

**Entrada válida**: `id * id + id`


## 📖 Referencias

- Aho, Lam, Sethi, Ullman - "Compilers: Principles, Techniques, and Tools"
