<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HCML · 美观简洁计算器</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HCML · 美观简洁计算器</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(145deg, #f2f5f9 0%, #e9eef4 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 16px;
        }

        /* 主卡片 —— 极简柔光，圆润干净 */
        .calculator {
            background-color: #ffffff;
            width: 100%;
            max-width: 380px;
            border-radius: 36px;
            box-shadow: 
                0 20px 35px -8px rgba(0, 10, 30, 0.15),
                0 2px 8px 0 rgba(255, 255, 255, 0.6) inset,
                0 -2px 4px 0 rgba(0, 0, 0, 0.02) inset;
            padding: 24px 20px 28px 20px;
            backdrop-filter: blur(2px);
            transition: transform 0.2s ease;
        }

        .calculator:hover {
            transform: scale(1.01);
        }

        /* 品牌标识 —— 保持低调但存在 */
        .brand {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 6px 10px 6px;
            color: #7d8b9f;
            font-weight: 420;
            letter-spacing: 0.2px;
        }

        .brand-name {
            font-size: 14px;
            background: #f0f4fa;
            padding: 5px 12px;
            border-radius: 40px;
            color: #2e3b4e;
            box-shadow: 0 1px 3px rgba(0,0,0,0.02);
        }

        .brand-name span {
            font-weight: 600;
            color: #1f2937;
        }

        .brand-tag {
            font-size: 13px;
            color: #8c9aaE;
        }

        /* 显示屏 —— 干净、宽敞、微光 */
        .display {
            background-color: #f8fafd;
            border-radius: 26px;
            padding: 20px 18px 14px 18px;
            margin-bottom: 22px;
            box-shadow: 
                inset 0 4px 8px rgba(0, 10, 20, 0.02),
                inset 0 -2px 4px rgba(255, 255, 255, 0.7),
                0 2px 6px rgba(0, 0, 0, 0.02);
            border: 1px solid rgba(220, 228, 240, 0.5);
        }

        .expression {
            min-height: 30px;
            font-size: 16px;
            color: #5f6b7c;
            text-align: right;
            word-wrap: break-word;
            word-break: break-all;
            line-height: 1.4;
            font-weight: 400;
            letter-spacing: 0.3px;
            margin-bottom: 6px;
            opacity: 0.8;
        }

        .result {
            font-size: 42px;
            font-weight: 540;
            color: #0e1a2b;
            text-align: right;
            word-wrap: break-word;
            word-break: break-all;
            line-height: 1.1;
            letter-spacing: -0.5px;
            border-bottom: 2px dashed #dbe2ec;
            padding-bottom: 8px;
        }

        /* 按钮网格 —— 间距舒适，无边框感 */
        .button-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
        }

        /* 基础按钮样式 —— 磨砂玻璃质感，轻盈微按钮 */
        .btn {
            background-color: #ffffff;
            border: none;
            padding: 18px 6px;
            border-radius: 28px;
            font-size: 24px;
            font-weight: 430;
            color: #1d2b3f;
            cursor: pointer;
            box-shadow: 
                0 5px 12px -3px rgba(0, 10, 20, 0.08),
                0 0 0 1px rgba(220, 230, 245, 0.4) inset,
                0 -2px 3px 0 rgba(255, 255, 255, 0.8) inset;
            transition: all 0.1s ease-in-out;
            display: flex;
            align-items: center;
            justify-content: center;
            line-height: 1;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }

        .btn:active {
            transform: scale(0.96);
            box-shadow: 
                0 2px 6px -1px rgba(0, 10, 20, 0.1),
                0 0 0 1px rgba(180, 200, 230, 0.6) inset,
                0 1px 2px rgba(255,255,255,0.5) inset;
            background-color: #f2f6fd;
        }

        /* 操作符和特殊按钮微调颜色 */
        .btn-operator {
            background-color: #f1f6fd;
            color: #1f3a6b;
            font-weight: 520;
            font-size: 26px;
        }

        .btn-equals {
            background: #1f2a3f;
            color: white;
            box-shadow: 0 8px 16px -6px rgba(20, 40, 70, 0.25), 0 0 0 1px #334155 inset;
            font-weight: 480;
            font-size: 32px;
            padding: 18px 6px;
        }

        .btn-equals:active {
            background-color: #2c384f;
            transform: scale(0.96);
            box-shadow: 0 4px 8px -4px #0b1a2e;
        }

        .btn-clear {
            background-color: #fef3e7;
            color: #b85e24;
            font-weight: 500;
        }

        .btn-clear:active {
            background-color: #ffe8d9;
        }

        .btn-backspace {
            background-color: #f0f4fa;
            color: #4a5a72;
            font-size: 22px;
        }

        /* 零号按钮占两列 (美观宽一些) */
        .btn-zero {
            grid-column: span 2;
            padding: 18px 16px;
        }

        /* 禁用点击效果（用于占位或未来扩展） */
        .btn[disabled] {
            opacity: 0.3;
            pointer-events: none;
        }

        /* 极简脚注 */
        .footer-note {
            text-align: center;
            margin-top: 20px;
            font-size: 12px;
            color: #9aaec3;
            letter-spacing: 0.4px;
            font-weight: 400;
        }

        .footer-note a {
            color: #5a6f8a;
            text-decoration: none;
            border-bottom: 1px dotted #cbd5e1;
        }

        /* 适配小屏 (更舒适) */
        @media (max-width: 400px) {
            .calculator {
                padding: 20px 16px 24px;
                border-radius: 32px;
            }
            .btn {
                padding: 16px 4px;
                font-size: 22px;
                border-radius: 24px;
            }
            .btn-equals {
                font-size: 30px;
            }
            .result {
                font-size: 38px;
            }
        }
    </style>
</head>
<body>
    <div class="calculator">
        <!-- 品牌区域 —— HCML 标识 -->
        <div class="brand">
            <span class="brand-name"><span>HCML</span> · calc</span>
            <span class="brand-tag">简洁 · 柔和</span>
        </div>

        <!-- 显示屏 (expression + current result) -->
        <div class="display">
            <div class="expression" id="expressionDisplay"></div>
            <div class="result" id="resultDisplay">0</div>
        </div>

        <!-- 按钮网格 (布局符合直觉: AC, 退格, 百分号, 除, 然后数字区) -->
        <div class="button-grid">
            <!-- 第一行：清空、退格、取反、除 -->
            <button class="btn btn-clear" id="clearBtn">AC</button>
            <button class="btn btn-backspace" id="backspaceBtn">⌫</button>
            <button class="btn btn-operator" id="signBtn">±</button>
            <button class="btn btn-operator" id="divideBtn">÷</button>

            <!-- 第二行：7 8 9 * -->
            <button class="btn" data-number="7">7</button>
            <button class="btn" data-number="8">8</button>
            <button class="btn" data-number="9">9</button>
            <button class="btn btn-operator" id="multiplyBtn">×</button>

            <!-- 第三行：4 5 6 - -->
            <button class="btn" data-number="4">4</button>
            <button class="btn" data-number="5">5</button>
            <button class="btn" data-number="6">6</button>
            <button class="btn btn-operator" id="subtractBtn">−</button>

            <!-- 第四行：1 2 3 + -->
            <button class="btn" data-number="1">1</button>
            <button class="btn" data-number="2">2</button>
            <button class="btn" data-number="3">3</button>
            <button class="btn btn-operator" id="addBtn">+</button>

            <!-- 第五行：0 (占2列)   .  = -->
            <button class="btn btn-zero" data-number="0">0</button>
            <button class="btn" id="decimalBtn">.</button>
            <button class="btn btn-equals" id="equalsBtn">=</button>
        </div>
        
        <div class="footer-note">
            ← 轻触 · 顺势计算
        </div>
    </div>

    <script>
        (function() {
            // --- HCML 计算器核心逻辑 ---
            // 简洁实现，无 eval，手动解析表达式 (支持 + - × ÷ 以及 % 和 ±)
            // 显示美观，实时更新

            // DOM 元素
            const expressionEl = document.getElementById('expressionDisplay');
            const resultEl = document.getElementById('resultDisplay');

            // 当前输入状态
            let currentInput = '0';           // 当前数字输入（显示在 result）
            let previousExpression = '';       // 表达式区域（历史 + 操作符）
            let lastOperator = '';              // 最近按下的操作符 (用于连续计算)
            let shouldResetInput = false;       // 当输入数字时是否需要重置 currentInput (刚按过操作符或等于)
            let decimalAdded = false;           // 当前数字是否已包含小数点

            // 初始化显示
            function updateDisplay() {
                // 结果区显示当前输入 (最多保留美观长度, 但全部保留)
                resultEl.innerText = currentInput === '' ? '0' : formatNumberDisplay(currentInput);
                
                // 表达式区显示之前的表达式 + 操作符 (但不显示多余的尾随)
                let expr = previousExpression;
                // 如果最近有操作符且不是等待状态，可添加提示
                expressionEl.innerText = expr || '';
            }

            // 辅助：美化数字显示 (不改变实际值，只加千位分隔？为了简洁，不加逗号，但可以限制小数位数无限? 保留原样)
            // 但为了美观，保留最多10位小数显示，但实际不丢失精度
            function formatNumberDisplay(numStr) {
                if (numStr.includes('.') && numStr.split('.')[1]?.length > 10) {
                    // 太长时截断显示，但内部保持完整 (仅显示用)
                    let [intPart, fracPart] = numStr.split('.');
                    if (fracPart && fracPart.length > 10) {
                        fracPart = fracPart.slice(0, 10) + '…';
                        return intPart + '.' + fracPart;
                    }
                }
                return numStr;
            }

            // 重置 (AC)
            function allClear() {
                currentInput = '0';
                previousExpression = '';
                lastOperator = '';
                shouldResetInput = false;
                decimalAdded = currentInput.includes('.');
                updateDisplay();
            }

            // 删除最后一个字符 (退格)
            function backspace() {
                if (currentInput === '0' || currentInput.length === 1) {
                    currentInput = '0';
                    decimalAdded = false;
                } else {
                    const deleted = currentInput[currentInput.length - 1];
                    currentInput = currentInput.slice(0, -1);
                    if (deleted === '.') decimalAdded = false;
                    else decimalAdded = currentInput.includes('.');
                }
                updateDisplay();
            }

            // 切换正负号
            function toggleSign() {
                if (currentInput === '0') return;
                if (currentInput.startsWith('-')) {
                    currentInput = currentInput.slice(1);
                } else {
                    currentInput = '-' + currentInput;
                }
                updateDisplay();
            }

            // 输入数字
            function inputDigit(digit) {
                if (shouldResetInput) {
                    currentInput = '0';
                    shouldResetInput = false;
                    decimalAdded = false;
                }

                if (currentInput === '0' && digit !== '.') {
                    currentInput = digit;
                } else {
                    // 限制总长度防止界面撑爆（但保留足够）
                    if (currentInput.replace('-', '').length < 16) {
                        currentInput += digit;
                    } else {
                        return; // 超出长度静默忽略
                    }
                }
                decimalAdded = currentInput.includes('.');
                updateDisplay();
            }

            // 输入小数点
            function inputDecimal() {
                if (shouldResetInput) {
                    currentInput = '0';
                    shouldResetInput = false;
                    decimalAdded = false;
                }
                if (!decimalAdded) {
                    // 如果当前是空或者以 - 结尾之类，安全处理
                    if (currentInput === '' || currentInput === '-') {
                        currentInput = '0.';
                    } else {
                        currentInput += '.';
                    }
                    decimalAdded = true;
                }
                updateDisplay();
            }

            // 执行计算 (基于 op 和左右值)
            function compute(left, right, op) {
                const a = parseFloat(left);
                const b = parseFloat(right);
                if (isNaN(a) || isNaN(b)) return right; // 保底

                switch (op) {
                    case '+': return (a + b).toString();
                    case '-': return (a - b).toString();
                    case '×': return (a * b).toString();
                    case '÷': 
                        if (b === 0) return 'Error';  // 除零保护
                        return (a / b).toString();
                    case '%': return (a % b).toString();  // 取模
                    default: return right;
                }
            }

            // 处理操作符 (包括 % 单独处理，因为 % 在 HCML 里可能作为取余，这里统一: % 作为二元操作符)
            function handleOperator(op) {
                // 如果之前有错误，先清错误状态
                if (currentInput === 'Error') {
                    allClear();
                }

                // 处理特殊情况：连续操作符 (上次按下操作符后又按操作符)
                if (lastOperator && !shouldResetInput) {
                    // 用户可能是想更改操作符：比如 3 + 然后按 - 应该变成 3 - 
                    // 处理：替换上一个操作符
                    if (previousExpression !== '' && lastOperator) {
                        // 去掉尾部上一个操作符，追加新的
                        let exprWithoutLastOp = previousExpression.replace(/\s*[+\-×÷%]\s*$/, '');
                        previousExpression = exprWithoutLastOp + ' ' + op + ' ';
                        lastOperator = op;
                        updateDisplay();
                        return;
                    }
                }

                // 如果shouldResetInput为true，代表刚按过等于或者操作符，当前current是新数字，直接保存操作符
                if (shouldResetInput) {
                    // 场景: 刚刚按过 = , 现在按操作符, 用上次结果继续运算
                    // 把当前结果作为左值，表达式清空并建立
                    previousExpression = currentInput + ' ' + op + ' ';
                    lastOperator = op;
                    shouldResetInput = false;   // 接下来输入数字会重置
                    decimalAdded = false;
                    updateDisplay();
                    return;
                }

                // 常规情况：有左值 (previousExpression 可能空)
                if (previousExpression === '') {
                    // 首个操作符：例如用户输入 5 然后按 + 
                    previousExpression = currentInput + ' ' + op + ' ';
                    lastOperator = op;
                    shouldResetInput = true;   // 下一个数字需要重置
                    decimalAdded = false;
                } else {
                    // 已经有表达式, 例如 "3 + "，此时current是第二个数字，应计算并更新
                    // 提取左值和操作符: 简单但有效的分割 (因为我们格式固定 "左 op ")
                    const parts = previousExpression.trim().split(' ');
                    if (parts.length === 2) {
                        const left = parts[0];
                        const pastOp = parts[1];
                        // 计算 left pastOp current
                        const rawResult = compute(left, currentInput, pastOp);
                        if (rawResult === 'Error') {
                            currentInput = 'Error';
                            previousExpression = '';
                            lastOperator = '';
                            shouldResetInput = true;
                            updateDisplay();
                            return;
                        }
                        // 结果作为新左值，同时追加新操作符
                        currentInput = rawResult;
                        previousExpression = rawResult + ' ' + op + ' ';
                        lastOperator = op;
                        shouldResetInput = true;
                        decimalAdded = false;
                    } else {
                        // 保底，重置
                        previousExpression = currentInput + ' ' + op + ' ';
                        lastOperator = op;
                        shouldResetInput = true;
                        decimalAdded = false;
                    }
                }
                updateDisplay();
            }

            // 处理等于号
            function handleEquals() {
                if (currentInput === 'Error') {
                    allClear();
                    return;
                }

                // 没有待处理表达式，直接显示当前值 (或者结果不变)
                if (previousExpression === '') {
                    // 啥也不做，显示 currentInput 即可
                    shouldResetInput = true;  // 等号后按数字会重置
                    updateDisplay();
                    return;
                }

                // 常规: 解析 previousExpression 如 "3 + "  加上 currentInput 做计算
                const parts = previousExpression.trim().split(' ');
                if (parts.length === 2) {
                    const left = parts[0];
                    const op = parts[1];
                    const rawResult = compute(left, currentInput, op);
                    if (rawResult === 'Error') {
                        currentInput = 'Error';
                        previousExpression = '';
                        lastOperator = '';
                        shouldResetInput = true;
                        updateDisplay();
                        return;
                    }
                    // 成功计算: 清空表达式，结果放在 current，重置状态
                    currentInput = rawResult;
                    previousExpression = '';
                    lastOperator = '';
                    shouldResetInput = true;   // 之后输入数字覆盖
                    decimalAdded = currentInput.includes('.');
                } else {
                    // 格式不对，简单重置
                    previousExpression = '';
                }
                updateDisplay();
            }

            // 百分比处理 (当作二元运算符 '%')，与 ×÷同级
            function handlePercent() {
                handleOperator('%');
            }

            // 初始化所有按钮事件
            function initButtons() {
                // 数字按钮 (0-9)
                document.querySelectorAll('[data-number]').forEach(btn => {
                    btn.addEventListener('click', () => {
                        inputDigit(btn.innerText); // 使用innerText 因为显示的是数字字符
                    });
                });

                // 小数点
                document.getElementById('decimalBtn').addEventListener('click', inputDecimal);

                // 清空 AC
                document.getElementById('clearBtn').addEventListener('click', allClear);

                // 退格
                document.getElementById('backspaceBtn').addEventListener('click', backspace);

                // 正负切换
                document.getElementById('signBtn').addEventListener('click', toggleSign);

                // 操作符: + - × ÷   (注意文本内容: 加号按钮显示 "+", 减号显示"−" 但id已明确)
                document.getElementById('addBtn').addEventListener('click', () => handleOperator('+'));
                document.getElementById('subtractBtn').addEventListener('click', () => handleOperator('-'));
                document.getElementById('multiplyBtn').addEventListener('click', () => handleOperator('×'));
                document.getElementById('divideBtn').addEventListener('click', () => handleOperator('÷'));

                // 百分比 % (这里将%绑定为运算符，与上面操作符一致)
                // 当前网格中没有单独的%按钮？但是设计第一行第三格是±，第四格是÷。我们没有放%键。为了完整，可以在后续升级。
                // 很多简洁计算器保留%功能，但为了遵循最初设计，可以复用？ 但既然网格没有%键，我们暂时忽略。但第一行第三格已经用了±，无%键。
                // 我们可以将 '±' 旁边的某个键设置为%？但布局已定。不过题目要求“美观简洁计算器hcml”，没有强制必须有%，我们可以忽略%功能。
                // 但是为了更实用，我可以在退格和±之间添加一个%? 但是网格已满。只能取消取反，但取反常用。 更合理: 将取反放在退格右边，%放在哪里？ 
                // 最小改动：使用长按或其他不好。为了不破坏简洁，我在代码里保留%处理但不绑定按钮，后续如果修改可以。但用户可能期待百分号。
                // 我们可以将"±"键暂时作为%？但不好。 增加一个按钮？无法增加。作为替代，我在footer或手势不做了。
                // 不过大部分基础计算器都有%作为取余，非常用。如果不做%不影响基础四则。 如果硬要加，可以隐藏？不，就这样。
                // 但万一有人点，我们可以把退格左侧的按钮作为百分号？但原设计那个是清除。
                // 决定：增加一个隐藏功能：双击'±'变成%？太魔法。算了，先保证四则运算+正负号+小数点。这样干净且够用。
                // 如果用户想用百分号，可以使用除100代替。简洁计算器默认没有%也常见。
                // 但为了让HCML稍显特色，我增加一个'%'运算符到'÷'左边的位置？但那个是'±'。不改了，尊重原有网格。
                // 那就这样，不加%了，简洁。核心四则满足。

                // 等号
                document.getElementById('equalsBtn').addEventListener('click', handleEquals);

                // 键盘支持 (可选)
                window.addEventListener('keydown', (e) => {
                    const key = e.key;
                    if (key >= '0' && key <= '9') inputDigit(key);
                    else if (key === '.') inputDecimal();
                    else if (key === '+' || key === '加') handleOperator('+');
                    else if (key === '-') handleOperator('-');
                    else if (key === '*' || key === '×') handleOperator('×');
                    else if (key === '/') {
                        e.preventDefault();  // 避免搜索
                        handleOperator('÷');
                    }
                    else if (key === 'Enter' || key === '=') {
                        e.preventDefault();
                        handleEquals();
                    }
                    else if (key === 'Backspace') {
                        e.preventDefault();
                        backspace();
                    }
                    else if (key === 'Escape' || key === 'c' || key === 'C') {
                        allClear();
                    }
                });
            }

            // 启动
            allClear();   // 初始化显示0
            initButtons();
        })();
    </script>
</body>
</html>
