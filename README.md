# 🚀 De Cero a CI/CD con Jenkins – E-commerce Full-Stack *Plaza China*

Implementación de un **pipeline CI/CD** para una app **Angular + Spring Boot** bajo principios **DevOps**.  
El foco está en la **automatización del ciclo de vida**: construir, probar, empaquetar y desplegar de forma **segura, trazable y reproducible**.

---

## 🎯 Objetivo
Adoptar una cultura DevOps usando **Jenkins** como orquestador CI/CD para garantizar **entregas continuas**, calidad consistente y despliegues confiables en entornos *staging* y *producción*.

---

## 🧱 Arquitectura (alto nivel)

- **Frontend:** Angular  
- **Backend:** Spring Boot (API REST)  
- **DB:** MySQL  
- **CI/CD:** Jenkins (Declarative Pipeline)  
- **Contenedores:** Docker + Docker Compose  
- **Repositorio:** GitHub (webhooks)  
- **Despliegue:** AWS EC2 (*staging* / *prod*)

---

## ⚙️ Flujo CI/CD con Jenkins

1. **Integración Continua (CI)**
   - Trigger por *webhook* de GitHub.  
   - Build frontend/backend + pruebas unitarias.  
   - Análisis estático con **SonarQube**.  
   - *Docker build* de imágenes.

2. **Entrega Continua (CD)**
   - Despliegue automático a **staging**.  
   - Pruebas *Smoke/E2E* y validación.  
   - Promoción manual y despliegue a **producción** (AWS EC2).

3. **Monitoreo & Feedback**
   - Tiempos de build/deploy, logs y notificaciones (Slack/Discord).  
   - Reportes de calidad y estado del pipeline.

---

## 🔁 Diagrama del Pipeline

```mermaid
graph TD
A[Commit GitHub] --> B[Build & Unit Tests]
B --> C[Code Analysis • SonarQube]
C --> D[Docker Build & Tag]
D --> E[Deploy Staging]
E --> F[Smoke/E2E Tests]
F --> G{Aprobación Manual}
G -->|Sí| H[Deploy Production]
G -->|No| E
H --> I[Monitoring & Feedback]
````

---

## 🧰 Herramientas

| Categoría          | Stack                               |
| ------------------ | ----------------------------------- |
| Orquestación CI/CD | **Jenkins** (Declarative Pipeline)  |
| Contenedores       | Docker, Docker Compose              |
| Repositorio        | GitHub + Webhooks                   |
| Calidad de código  | SonarQube                           |
| Pruebas            | JUnit (BE), Jasmine/Karma (FE), E2E |
| Infraestructura    | AWS EC2                             |
| App                | Angular, Spring Boot, MySQL         |

---

## 📊 Beneficios del enfoque DevOps

* **Automatización de punta a punta**: menos riesgo manual.
* **Ciclos de entrega más cortos** y previsibles.
* **Calidad validada** en cada commit (tests + análisis).
* **Entornos reproducibles** vía Docker.
* **Trazabilidad total** del cambio a producción.

---

## 📈 Métricas de éxito (esperadas)

* Reducción > **60%** en tiempo de despliegue manual.
* Integraciones verificadas en cada commit.
* *Mean Lead Time* y *Change Failure Rate* a la baja.
* Pipeline reproducible para *staging* y *prod*.

---

## 📂 Estructura del repositorio

```
.
├── backend/               # API Spring Boot
├── frontend/              # App Angular
├── Jenkinsfile            # Pipeline declarativo
├── docker-compose.yml     # Orquestación local/Jenkins
├── sonar-project.properties
└── README.md
```

---

## 🚀 Ejecución del pipeline (local/Jenkins)

```bash
# Clonar
git clone https://github.com/usuario/plaza-china-cicd.git
cd plaza-china-cicd

# Levantar Jenkins (ejemplo)
docker-compose up -d jenkins

# Configurar webhook en GitHub -> Jenkins
# Crear pipeline multibranch o pipeline desde Jenkinsfile

# Ejecutar
# Jenkins > Build Now
```

---

## 🧠 Lecciones clave

* **Jenkinsfile declarativo** simplifica auditoría y mantenimiento.
* **Shift-left** de calidad/seguridad reduce retrabajo.
* **Promoción por etapas** (staging → prod) mejora confiabilidad.

---

## 🏁 Resultado

Pipeline **CI/CD** funcional y escalable que soporta el desarrollo, validación y despliegue de un e-commerce full-stack, fortaleciendo una **cultura DevOps** con entregas continuas y trazables.
