---
layout: post
author: aaf925
title: "Guía Básica de SonarQube"
date: 2025-04-02
pin: true
math: false
mermaid: false
---

SonarQube es una plataforma de inspección continua de calidad de código que ayuda a detectar bugs, vulnerabilidades y code smells en 20+ lenguajes de programación.
---

## 🚀 1. Instalación Rápida
```bash
# Descargar versión Community (requiere Java 11+)
docker pull sonarqube:community

# Ejecutar contenedor (puerto 9000 por defecto)
docker run -d -p 9000:9000 --name sonarqube sonarqube:community
```

## 🔧 2. Configuración Inicial

    Cambiar contraseña de admin en primer login

    Crear proyecto manual o vinculando repositorio

    Generar token de seguridad para análisis

    Seleccionar lenguaje y metodología de análisis

## 📊 3. Análisis de Código
```bash
# Ejemplo para proyecto Java (Maven)
mvn clean verify sonar:sonar \
  -Dsonar.projectKey=mi-proyecto \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=TU_TOKEN
```

## 🔍 4. Métricas Clave

✔ Bugs: Errores reales en tiempo de ejecución
✔ Vulnerabilidades: Problemas de seguridad
✔ Code Smells: Malas prácticas mantenibles
✔ Cobertura: % de código testeado
✔ Duplicación: Código repetido

## 🛡️ 5. Reglas Comunes
```bash
// Ejemplo de detección en Java
if (condición) {           // Code smell: condiciones redundantes
    return true;
} else {
    return false;
}
```

## ⚙️ 6. Integración con CI/CD
```bash
# Ejemplo para GitHub Actions
- name: SonarQube Scan
  uses: SonarSource/sonarqube-scan-action@master
  env:
    SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
    SONAR_HOST_URL: ${{ secrets.SONAR_HOST_URL }}
```