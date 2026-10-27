# test-driven-development

> Que el agente escriba primero la prueba que demuestra el comportamiento, y después el código.

**Desarrollo guiado por pruebas (TDD)** · Skill para agentes de código de la comunidad [nvvdev](https://github.com/nvv-dev). Funciona en Claude Code como plugin o como skill suelta, y en cualquier agente compatible con el formato abierto [`SKILL.md`](https://agentskills.io).

*English summary at the end.*

## Qué hace

Guía al agente por ciclos rojo-verde-refactor: escribe una prueba, la ve fallar por la razón correcta, escribe el mínimo código para que pase y luego mejora el diseño con todo en verde. Prueba por la frontera pública del módulo, no por sus detalles internos, y prohíbe debilitar pruebas para que pasen.

## Objetivo

Que cada cambio llegue con pruebas que realmente protegen el comportamiento, y que una corrección de bug empiece por una prueba que reproduce el bug.

## Cuándo usarla

- Implementas una funcionalidad con criterios de aceptación claros
- Corriges un bug que se puede reproducir
- Cambias lógica de negocio que ya tiene pruebas

## Cuándo no

- Prototipos desechables o pruebas de concepto
- Cambios solo de configuración o de estilos

## Ejemplo

```text
Implementa la regla "no se puede vender si no hay stock" en OrderService usando TDD.
```

## Cómo se activa

Esta skill **se activa sola**: Claude Code lee su descripción y la carga cuando la tarea coincide. También puedes pedirla por nombre ("usa la skill test-driven-development") o invocarla con `/test-driven-development:test-driven-development` (plugin) o `/test-driven-development` (copiada a `.claude/skills/`).

## Instalación

### Opción 1: Claude Code, como plugin (recomendada)

Dentro de Claude Code:

```text
/plugin marketplace add nvv-dev/claude-plugins
/plugin install test-driven-development@nvvdev
```

La primera línea agrega el catálogo de nvvdev una sola vez; la segunda instala esta skill. Si prefieres el paquete completo, instala `dev-workflow@nvvdev` en su lugar (incluye esta skill y las demás de [dev-workflow](https://github.com/nvv-dev/dev-workflow)); no instales los dos a la vez.

### Opción 2: Claude Code, copiando la skill

Para un solo proyecto (se comparte con tu equipo por git):

```bash
git clone --depth 1 https://github.com/nvv-dev/test-driven-development.git /tmp/test-driven-development
mkdir -p .claude/skills
cp -R /tmp/test-driven-development/skills/test-driven-development .claude/skills/
```

Para todos tus proyectos, cópiala en `~/.claude/skills/` en lugar de `.claude/skills/`.

### Opción 3: otros agentes

Copia la carpeta `skills/test-driven-development/` en la carpeta de skills de tu agente (cada agente documenta la suya). Con la CLI [skills](https://github.com/vercel-labs/skills) de Vercel Labs:

```bash
DISABLE_TELEMETRY=1 npx skills add nvv-dev/test-driven-development
```

### Verificar

Abre una sesión nueva y pregunta "¿qué skills tienes disponibles?"; `test-driven-development` debe aparecer. Con el plugin, `/plugin` la muestra como instalada.

### Actualizar o desinstalar

- Plugin: `/plugin marketplace update nvvdev` para actualizar; `/plugin uninstall test-driven-development@nvvdev` para quitarla.
- Copia manual: repite la copia para actualizar, o borra la carpeta `.claude/skills/test-driven-development`.

Antes de instalar cualquier skill, incluida esta, conviene leerla: es un solo archivo, [`skills/test-driven-development/SKILL.md`](skills/test-driven-development/SKILL.md). Ver [vetting-external-skills](https://github.com/nvv-dev/vetting-external-skills).

## Contenido

| Ruta | Qué es |
|---|---|
| `skills/test-driven-development/SKILL.md` | La skill: instrucciones en inglés para que los escáneres de seguridad las analicen completas; el agente responde en tu idioma |
| `.claude-plugin/plugin.json` | Manifiesto para instalarla como plugin |
| `.github/workflows/` | Validación de estructura y escaneo con SkillSpector en cada cambio |

## Contribuir

Este repo se **genera** desde [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow), donde vive la versión canónica. Abre issues y PRs allí. La mejor contribución es un caso real en la sección *Known failures* de la skill, con la regla que lo evita.

## Origen

Escrita desde cero por nvvdev. Inspirada en: [obra/superpowers](https://github.com/obra/superpowers) (test-driven-development), [mattpocock/skills](https://github.com/mattpocock/skills) (tdd).

## Licencia

MIT.

---

## English

**test-driven-development** — Drives work as red-green-refactor cycles at the module's public boundary, and forbids weakening tests to get green.

Install in Claude Code with `/plugin marketplace add nvv-dev/claude-plugins` and `/plugin install test-driven-development@nvvdev`, or copy `skills/test-driven-development/` into `.claude/skills/` (project) or `~/.claude/skills/` (personal). Other agents: copy the folder into their skills directory, or run `DISABLE_TELEMETRY=1 npx skills add nvv-dev/test-driven-development`. Loads automatically when the task matches its description. Canonical source: [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow). License: MIT.
